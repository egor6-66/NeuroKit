---
name: keep-blocking-io-off-the-event-loop
description: Keep the asyncio event loop responsive when a coroutine reads from disk or waits on a network service.
---

Use the library’s async API when it provides one and await the operation. When an existing synchronous I/O call can block, pass the callable and its arguments to `asyncio.to_thread` or the project’s thread-pool helper. Calling the function while constructing those arguments still runs it on the event loop. Quick operations such as building a path can stay inline.

For example, a coroutine can read a header from a blocking binary stream while other requests continue to run:

```python
import asyncio
from typing import BinaryIO


async def read_header(source: BinaryIO) -> bytes:
    return await asyncio.to_thread(source.read, 16)
```

If a synchronous helper already handles an entire file copy, dispatch that helper once so its open, read, write, and close operations stay together.

[Python documentation on running blocking I/O in a thread](https://docs.python.org/3.13/library/asyncio-task.html#asyncio.to_thread)
