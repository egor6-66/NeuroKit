---
name: define-command-inputs-explicitly
description: Keep a command's accepted fields explicit as the entity evolves.
---

Define the input from the operations the command supports. Use Pick when the accepted fields share their meaning and types with the entity. Add Partial when each selected field may be omitted. Define a separate input type for fields with command-specific meanings or formats.

```ts
type Agent = {
  id: string
  name: string
  description: string
  createdAt: string
}

type UpdateAgentInput = Partial<Pick<Agent, 'name' | 'description'>>
```

Adding ownerId to Agent leaves the update contract unchanged. Partial<Agent> and an Omit-based exclusion list would automatically include the new field. Pick describes a static type. Validate or select incoming fields at runtime when the command boundary requires it.

[TypeScript Handbook — Utility Types](https://www.typescriptlang.org/docs/handbook/utility-types.html)
