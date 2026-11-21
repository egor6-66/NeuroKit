---
name: type-known-dictionary-fields
description: Use TypedDict for dictionaries with known fields and field-specific value types.
---

When a function accepts or returns a dictionary with known fields, reuse the `TypedDict` that describes them, or define one if needed. For a partial update where callers may omit any field, use `total=False`. A field accepts `None` only if its value type allows it.

```python
from typing import TypedDict


class AgentChanges(TypedDict, total=False):
    name: str
    avatar: str | None


rename: AgentChanges = {"name": "Atlas"}
clear_avatar: AgentChanges = {"avatar": None}
```

In this update, omitting `avatar` keeps the current avatar and passing `None` clears it. With this annotation, mypy flags a misspelled key such as `nmae` and an invalid value such as `{"name": None}`. For a lookup table that maps arbitrary agent IDs to names, `dict[str, str]` already expresses the contract.

[Python documentation on TypedDict](https://docs.python.org/3.13/library/typing.html#typing.TypedDict)
