---
name: consume-iterable-inputs-once
description: Make functions that accept Iterable work with one-pass inputs such as generators.
---

An `Iterable` can be a generator. Count, filter, or collect from it in one pass when possible. For example, counting items with `sum(1 for _ in names)` exhausts a generator before a second loop can build a preview.

```python
from collections.abc import Iterable


def preview_names(names: Iterable[str], limit: int) -> tuple[int, list[str]]:
    total = 0
    preview = []
    for name in names:
        total += 1
        if len(preview) < limit:
            preview.append(name)
    return total, preview
```

If later steps genuinely need repeated access, collect the values once at the point of reuse. If the operation requires positional access from its caller, express that requirement with `Sequence`.

Verify with both a list and a generator over the same values. Both should report the full count and the same preview, including when the input is empty.

[Python documentation on iterators](https://docs.python.org/3.13/glossary.html#term-iterator)
