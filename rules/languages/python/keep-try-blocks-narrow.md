---
name: keep-try-blocks-narrow
description: Limit a try block to the operation whose expected exceptions the handler can explain or recover from.
---

Identify what the handler promises to the caller. If it reports an unreadable input file, put the decoding or parsing operation inside `try` and catch the exceptions that indicate malformed input. Keep subsequent processing outside that block so its failures retain their own meaning.

```python
from collections.abc import Callable

import yaml


class UnreadableRule(ValueError):
    pass


def import_rule(text: str, save: Callable[[object], None]) -> None:
    try:
        document = yaml.safe_load(text)
    except yaml.YAMLError as error:
        raise UnreadableRule("Invalid rule YAML") from error

    save(document)
```

Check both paths. Malformed YAML should raise `UnreadableRule` before `save` runs. With valid input, an error raised by `save` must reach the caller unchanged, even if it also happens to be a `yaml.YAMLError`.

[Python documentation on handling exceptions](https://docs.python.org/3.13/tutorial/errors.html#handling-exceptions)
