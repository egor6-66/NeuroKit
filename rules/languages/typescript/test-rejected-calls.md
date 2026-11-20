---
name: test-rejected-calls
description: Test the invalid call a TypeScript contract is meant to reject.
---

When a type contract promises to reject a specific use, cover that use in the type tests written after feature acceptance. Import the actual API under test. Put a valid call beside the invalid call and vary only the condition under test.

```ts
runSteps([build])

// @ts-expect-error At least one step is required.
runSteps([])
```

Run the fixture through the project's type checker. If the API starts accepting the invalid call, TypeScript reports the unused directive. Keep the rejected expression small: any diagnostic on the following line can satisfy the directive, including one unrelated to the contract.

[TypeScript — ts-expect-error comments](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-3-9.html#ts-expect-error-comments)
