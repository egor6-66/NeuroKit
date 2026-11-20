---
name: use-generics-to-express-relationships
description: Use type parameters to express relationships the implementation preserves.
---

Introduce a type parameter when it connects arguments, callback results, or container elements. For a generic return type, identify how the implementation obtains a value of that type.

```ts
function first<T>(items: readonly T[]): T | undefined {
  return items[0]
}

function parseWith<T>(text: string, decode: (value: unknown) => T): T {
  const value: unknown = JSON.parse(text)
  return decode(value)
}
```

The array supplies the element type for first. The decoder supplies the result type for parseWith and is responsible for validating the parsed value.

A caller-selected type can promise more than the implementation delivers:

```ts
function parseJson<T>(text: string): T {
  return JSON.parse(text)
}

const count = parseJson<number>('"hello"')
```

This compiles because JSON.parse returns any. The runtime value is a string even though count has the static type number.

[TypeScript Handbook — Guidelines for Writing Good Generic Functions](https://www.typescriptlang.org/docs/handbook/2/functions.html#guidelines-for-writing-good-generic-functions)
