---
name: model-optional-properties
description: Preserve the meaning of omitted keys and explicit values when constructing objects.
---

Use an optional property when the caller may omit its key. Include null or explicit undefined in the value type when the contract gives that value a meaning. Preserve the distinction when constructing or merging objects.

```ts
type AgentPatch = { avatarUrl?: string | null }

const keep: AgentPatch = {}
const replace: AgentPatch = { avatarUrl: '/avatars/new.png' }
const clear: AgentPatch = { avatarUrl: null }
```

In this patch contract, omission keeps the current avatar and null clears it. When a form leaves the avatar untouched, omit the key. Converting a missing form value to null with ?? would request deletion.

With exactOptionalPropertyTypes enabled, TypeScript rejects an explicit undefined for avatarUrl in this example. Without that option, the assignment is permitted. In JavaScript, a presence check distinguishes an omitted key from one set to undefined in either case.

[TypeScript — exactOptionalPropertyTypes](https://www.typescriptlang.org/tsconfig/exactOptionalPropertyTypes.html)
