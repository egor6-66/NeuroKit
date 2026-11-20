---
name: accept-readonly-arrays
description: Accept readonly arrays when a function preserves the caller's collection.
---

Use readonly T[] for an array parameter when the function should preserve its order and membership. Both mutable and readonly arrays can be passed to that parameter. Read or filter the array directly. When sorting for display, sort a copy or use a supported non-mutating sorting method.

```ts
type Agent = { name: string }

function agentsByName(agents: readonly Agent[]): Agent[] {
  return [...agents].sort((a, b) => a.name.localeCompare(b.name))
}
```

The readonly modifier constrains writes to the array through this parameter. The element objects retain their own property types. When changing the caller's array in place is part of the contract, use T[] and make that effect clear to callers.

[TypeScript Handbook — ReadonlyArray](https://www.typescriptlang.org/docs/handbook/2/objects.html#the-readonlyarray-type)
