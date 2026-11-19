---
name: model-state-variants
description: Use a discriminated union when required fields depend on the variant.
---

When a value has distinct variants with different required fields, describe each variant as a union member. Give them a shared discriminant with a distinct literal value for each variant. Keep a property optional when it can genuinely be absent within that variant.

```ts
type LaunchResult =
  | { status: 'started'; runId: string }
  | { status: 'failed'; message: string }
```

Checking status narrows the result. The started branch can use runId directly, and the failed branch can use message directly.

[TypeScript Handbook — Discriminated unions](https://www.typescriptlang.org/docs/handbook/2/narrowing.html#discriminated-unions)
