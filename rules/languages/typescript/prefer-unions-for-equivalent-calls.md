---
name: prefer-unions-for-equivalent-calls
description: Use a union parameter for equivalent calls and overloads to express meaningful differences between call signatures.
---

When calls have the same parameter structure and result type and only one argument accepts several types, describe that argument with a union. A caller whose value already has the union type can then pass it directly.

```ts
type Agent = { name: string }
declare function findById(id: string | number): Agent | undefined
```

Consider overloads when the argument combination determines the result type. Describe each supported call precisely enough for callers to use its result directly.

```ts
declare function readFile(path: string): Promise<Uint8Array>
declare function readFile(path: string, encoding: 'utf8'): Promise<string>
```

In this API, passing the encoding selects a string result. Omitting it selects bytes.

[TypeScript Handbook — Writing Good Overloads](https://www.typescriptlang.org/docs/handbook/2/functions.html#writing-good-overloads)
