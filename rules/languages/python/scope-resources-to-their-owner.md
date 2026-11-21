---
name: scope-resources-to-their-owner
description: Close resources acquired by a function on every exit and keep borrowed resources available to their caller.
---

Use `with` or `async with` where the owning code acquires a file, client, or stream. Keep cleanup in that scope so an early return or an exception still releases the resource. A resource supplied by the caller stays open for the caller unless the API explicitly transfers ownership.

For example, a function that reads a member of an open ZIP archive owns the member stream. The caller owns the archive and can read another member even if the first read fails.

```python
from zipfile import ZipFile


def read_member(archive: ZipFile, name: str, limit: int) -> bytes:
    with archive.open(name) as member:
        data = member.read(limit + 1)
        if len(data) > limit:
            raise ValueError("member exceeds size limit")
        return data
```

The same boundary applies to streaming HTTP responses. A helper that receives a shared client can use `async with` around the response stream it opens.

[Python documentation on the with statement](https://docs.python.org/3.13/reference/compound_stmts.html#the-with-statement)
