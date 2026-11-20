---
name: express-required-elements
description: Use a non-empty tuple when an operation requires at least one element.
---

When a collection parameter must contain at least one element, express that requirement with a tuple containing a required first element and a rest element.

```ts
type Step = () => void

function runSteps(steps: readonly [Step, ...Step[]]) {
  const [first, ...rest] = steps
  first()
  for (const step of rest) step()
}
```

Use an ordinary array when an empty list is valid. For a list of unknown length, check that it contains an element before passing it to an operation that requires one. A tuple assertion alone cannot guarantee that a first element exists at runtime.

[TypeScript Handbook — Tuple Types](https://www.typescriptlang.org/docs/handbook/2/objects.html#tuple-types)
