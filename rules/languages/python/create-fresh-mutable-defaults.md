---
name: create-fresh-mutable-defaults
description: Give each independent call or dataclass instance its own mutable defaults.
---

Python evaluates a function default once, when the function is defined. If a call owns its results, create the collection inside the function. If callers can supply a collection to update, use `None` as the default when it means “no collection supplied”. Check `is None` so an explicitly supplied empty collection keeps its identity.

```python
from dataclasses import dataclass, field


def record_skip(path: str, skipped: list[str] | None = None) -> list[str]:
    if skipped is None:
        skipped = []
    skipped.append(path)
    return skipped


@dataclass
class Preview:
    items: list[str] = field(default_factory=list)
```

`default_factory=list` creates a list for each preview. If two operations intentionally accumulate into the same list, let the caller own it and pass it explicitly.

Verify that a second independent call starts fresh, that changing one preview leaves another untouched, and that a supplied empty list receives the update.

[Python function defaults](https://docs.python.org/3.13/tutorial/controlflow.html#default-argument-values) · [Dataclass default factories](https://docs.python.org/3.13/library/dataclasses.html#default-factory-functions)
