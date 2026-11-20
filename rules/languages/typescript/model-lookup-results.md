---
name: model-lookup-results
description: Reflect a possible lookup miss in the return type.
---

When an entity can be absent, expose that outcome in the lookup signature so callers can handle it. For example, keep the undefined returned by Map.get:

```ts
type AgentId = string
type Agent = { id: AgentId; name: string }
const agentsById = new Map<AgentId, Agent>()

function findById(id: AgentId): Agent | undefined {
  return agentsById.get(id)
}
```

If a method promises an Agent on every successful call, establish that guarantee. When absence is an error, check the lookup result inside the method and report the missing ID. A non-null assertion only changes the static type; it cannot enforce the guarantee at runtime.

[TypeScript Handbook — Non-null Assertion Operator](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#non-null-assertion-operator-postfix-)
