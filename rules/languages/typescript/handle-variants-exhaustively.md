---
name: handle-variants-exhaustively
description: Make the compiler flag missing cases when every union member needs a decision.
---

When each union member needs a value, use an exhaustive mapping. When each member needs its own behavior, use a switch and check the remaining value against never after the returning branches.

```ts
type RunStatus = 'running' | 'failed'

const labels = {
  running: 'Running',
  failed: 'Failed',
} satisfies Record<RunStatus, string>

function report(status: RunStatus, onProgress: () => void, onError: () => void) {
  switch (status) {
    case 'running': return onProgress()
    case 'failed': return onError()
  }
  status satisfies never
}
```

Adding a status requires a decision in both places. A predicate asking only whether a run is active can simply compare the status to 'running'.

[TypeScript Handbook — Exhaustiveness checking](https://www.typescriptlang.org/docs/handbook/2/narrowing.html#exhaustiveness-checking)
