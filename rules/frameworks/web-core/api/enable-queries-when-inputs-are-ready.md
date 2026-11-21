---
name: enable-queries-when-inputs-are-ready
description: Enable a dependent web-core query when all required inputs are ready and show a prompt while the user still needs to make a selection.
---

Set `enabled` in the reactive options of an `@web-core/query` query that depends on a selection or another result. Evaluate readiness using the input contract. For example, if a run history query requires a nonempty agent ID, read the selected ID inside the options function and set `enabled` to `agentId.length > 0` when an empty string represents no selection.

Use the same readiness condition to decide what the panel shows. While the selection is empty, show “Select an agent”. A disabled query with no cached data can have `isPending` set to true even while idle. Once the inputs are ready, use `isPending && isFetching` to indicate an active first fetch.

Verify with an uncached agent. Open the history panel with no selection and check that it shows the prompt and sends no history request. Select the agent and check that the request carries its ID. Clear the selection while the request is in flight. The prompt should return immediately and remain visible when the earlier request settles.
