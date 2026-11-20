---
name: narrow-by-intent
description: Choose a narrowing condition that preserves meaningful falsy values.
---

Choose the condition from the contract. When a branch depends on whether a value was supplied, check explicitly for the absence values the type permits. Consider how the branch should behave for zero, false, or an empty string whenever those are valid inputs.

```ts
function resolveRetryCount(retryCount: number | undefined): number {
  return retryCount ?? 3
}
```

Here zero disables retries and undefined selects the default. Using || would enable three retries for both inputs. Use ?? when null and undefined should both trigger a fallback, or when the type allows only one of them. If they mean different things, handle them separately. A truthiness check is appropriate when its meaning matches the condition, for example if (enabled) for an on/off flag.

[TypeScript Handbook — Truthiness narrowing](https://www.typescriptlang.org/docs/handbook/2/narrowing.html#truthiness-narrowing)
