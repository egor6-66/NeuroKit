---
name: key-queries-by-input
description: Key cached queries by the resource and the inputs that identify the requested data.
---

Include the resource and the request parameters that distinguish independently cached results in the query key. Inside the reactive options function, prepare the inputs once and use the same values for the key and the API call.

```ts
import { createQuery } from '@web-core/query'

const query = createQuery(() => {
  const projectId = props.projectId
  return {
    queryKey: ['agents', projectId],
    queryFn: () => listAgents(projectId),
  }
})
```

For a server-side search, include the submitted search term in the key. A filter applied only to an already loaded list belongs to presentation state and can reuse the same cache entry.

Verify the transition from project A to B and back to A. Each selected project must display its own agents, including when an earlier request completes after the selection changes.
