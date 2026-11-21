---
name: name-easily-confused-arguments
description: Use keyword arguments when swapping two positional values would look valid and change the meaning of the call.
---

Name arguments at the call site when their roles are easy to confuse. For example, the owner ID and agent ID in a lookup are both strings. Writing `owner_id=caller.owner_id` and `agent_id=agent_id` makes the mapping visible during review.

For a new API, place `*` before parameters that should always be named. Positional arguments still work well when their meaning is clear.

```python
def agent_key(*, owner_id: str, agent_id: str) -> tuple[str, str]:
    return owner_id, agent_id


key = agent_key(owner_id="team-a", agent_id="atlas")
```

For an existing API that accepts both positional and keyword arguments, start by naming the arguments in calls you edit. Adding `*` to its signature breaks existing positional callers and requires a compatible migration.

[Python documentation on keyword-only arguments](https://docs.python.org/3.13/tutorial/controlflow.html#keyword-only-arguments)
