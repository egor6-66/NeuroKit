---
name: derive-reactive-values
description: Derive values from reactive inputs and reserve writable signals for values that change independently.
---

When existing signals, stores, or props fully determine a value, express the calculation as a function that reads those inputs when called. Use createMemo from @web-core/solid when consumers benefit from sharing a cached calculation. Keep the calculation pure. An effect that copies the result into another signal introduces a setter and a synchronization step.

For example, if the agents module exposes a reactive lookup, the selected agent can follow the selected ID and the current entity data:

```tsx
const selectedAgent = () => agents.findById(selectedId())
```

Read selectedAgent() in JSX or another reactive consumer. Keep entity lookup in the agents module.

Give a value its own writable state when there is an independent action that changes it. A form draft can start with an agent's saved name and then change as the user types. Initialize or reset it at a deliberate editing boundary so a background refresh preserves unsaved input.

[Solid — Derived signals](https://docs.solidjs.com/concepts/derived-values/derived-signals) · [Solid — createMemo](https://docs.solidjs.com/reference/basic-reactivity/create-memo)
