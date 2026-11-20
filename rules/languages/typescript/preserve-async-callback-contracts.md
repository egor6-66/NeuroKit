---
name: preserve-async-callback-contracts
description: Express callback completion in its type when later steps depend on the outcome.
---

TypeScript allows an async function where a callback returning void is expected. The caller can discard the returned promise and move on while the operation is still running.

When a later step depends on an asynchronous callback succeeding, accept a callback returning Promise<void> and await it before taking that step. If synchronous callbacks are also supported, use void | Promise<void> as the return type and await the result in either case.

```ts
async function submit(onSave: () => Promise<void>, closeEditor: () => void) {
  await onSave()
  closeEditor()
}
```

A failed save leaves the editor open and rejects the promise returned by submit. The caller can await it and report the error. When an external event API discards callback results, handle rejection at that boundary, for example with a synchronous listener that calls submit(onSave, closeEditor).catch(showSaveError). Writing void before a promise expression alone leaves rejection unhandled.

[TypeScript Handbook — Return type void](https://www.typescriptlang.org/docs/handbook/2/functions.html#return-type-void)
