---
name: design-slice-public-api
description: Expose the operations, components, and types that consumers need through the slice's public API.
---

Give external consumers an explicit entry point. Import from that entry point whenever crossing the slice boundary, including for types. Export by name the operations, components, hooks, and types that support actual consumer use cases.

Keep hooks, stores, setters, and helpers used only within the entity private to its slice. When a consumer needs new behavior, identify the operation it needs and expose that operation. For example, a page looking up an agent by ID can call findAgentById while the entity owns the backing collection.

```ts
// entities/agent/index.ts
export { findAgentById } from './model/find-agent-by-id'
export type { Agent } from './model/types'
```

Within the slice, import sibling modules directly using relative paths. Importing the slice's own public index from one of its implementation modules can create a cycle. Keep exports explicit so adding an internal helper does not silently expand the public API.

[FSD — Define a strict public API](https://feature-sliced.design/docs/get-started/tutorial#define-a-strict-public-api)
