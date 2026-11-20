---
name: derive-types-from-source
description: Derive literal unions from their canonical values and check independently selected subsets against their contract.
---

When a runtime list and a type represent the same set and must evolve together, define the values once. Use a const assertion to retain the literal types and indexed access to derive the element union.

```ts
const launchModes = ['manual', 'scheduled'] as const
type LaunchMode = (typeof launchModes)[number]
```

When an existing contract owns the full set and a consumer chooses a subset, reuse the contract type. Check the selected values with satisfies. Adding a mode to the contract should leave that consumer's choices unchanged until it opts in.

```ts
// ApiLaunchMode represents the type supplied by the API contract.
type ApiLaunchMode = 'manual' | 'scheduled' | 'on-create'
const formModes = ['manual', 'scheduled'] as const satisfies readonly ApiLaunchMode[]
```

[TypeScript Handbook — Indexed Access Types](https://www.typescriptlang.org/docs/handbook/2/indexed-access-types.html)
