---
name: refresh-affected-queries
description: Keep cached details and lists consistent after a successful mutation through web-core query.
---

When implementing a mutation, identify the detail and list queries that can become stale on success. Keep cache updates with the owning entity operation so every caller gets the same behavior.

If the server returns the complete canonical value for a cached detail, update that entry using its existing key and queryClient.setQueryData. If the response only acknowledges success, invalidate the affected query through @web-core/query. Reuse the existing query keys and scope invalidation to the affected data.

For example, renaming an agent can change its position in a sorted list or its membership in a filtered list. Invalidate the affected list queries when updating them by hand would require duplicating the server's sorting or filtering logic.

Verify the mutation with the detail and list already open. After the rename succeeds, check the displayed name and the agent's position or membership under the active sort or filter, without reloading the page.
