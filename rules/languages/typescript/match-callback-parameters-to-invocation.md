---
name: match-callback-parameters-to-invocation
description: Declare callback parameters according to the arguments the caller supplies.
---

If the caller always supplies an argument, declare it as required in the callback signature. Each handler may omit trailing parameters it does not use. Mark a parameter optional only when invoking the callback without that argument is valid.

```ts
type OnSelect = (agent: Agent, index: number) => void

const openSelected: OnSelect = agent => openAgent(agent)
const markSelected: OnSelect = (agent, index) => markRow(index, agent.id)
```

The list supplies the index on every selection. A handler that uses the index can rely on receiving a number.

[TypeScript Handbook — Optional Parameters in Callbacks](https://www.typescriptlang.org/docs/handbook/2/functions.html#optional-parameters-in-callbacks)
