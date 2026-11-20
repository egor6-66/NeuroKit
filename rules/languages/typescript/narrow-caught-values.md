---
name: narrow-caught-values
description: Narrow caught values before accessing their fields and propagate failures the caller cannot handle.
---

Treat a caught value as unknown. Before reading fields such as message, code, or fields, establish their type with a runtime check. Use the project's error class or the library's type guard when available. A type assertion such as error as Error provides no runtime check.

```ts
try {
  await createAgent(input)
} catch (error: unknown) {
  if (error instanceof ValidationError) {
    showFieldErrors(error.fields)
    return
  }
  throw error
}
```

Here the form knows how to display a validation error. Rethrowing the original value lets the caller handle other failures with their original details.

[TypeScript — useUnknownInCatchVariables](https://www.typescriptlang.org/tsconfig/useUnknownInCatchVariables.html)
