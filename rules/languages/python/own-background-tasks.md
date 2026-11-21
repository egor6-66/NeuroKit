---
name: own-background-tasks
description: Give each asyncio task an owner that observes failures and waits for cleanup when its work ends.
---

Choose the owner according to how long the work should live. A WebSocket connection can own its event sender. Work intended to outlive a request belongs to a longer-lived owner that observes the result and joins the task during shutdown.

For related tasks with a shared lifetime, use an `asyncio.TaskGroup`. In this example `wait_for_disconnect()` returns when the client leaves. The group would wait indefinitely for an idle sender on normal exit, so the connection explicitly requests cancellation:

```python
async with asyncio.TaskGroup() as tasks:
    sender = tasks.create_task(send_events())
    await wait_for_disconnect()
    sender.cancel()
```

Leaving the group waits for the sender to finish its cleanup. If the sender raises an unexpected exception while the connection is open, the group interrupts the waiting operation and propagates the failure to its caller. For a manually managed task, retain the handle, observe its outcome, and await it after requesting cancellation.

Verify both exits. Disconnect an idle client and check that the sender has finished cleanup before the handler returns. Make the sender fail while the client is still connected and check that the owner receives the error without waiting for a disconnect.

[Python documentation on task groups and cancellation](https://docs.python.org/3.13/library/asyncio-task.html#task-groups)
