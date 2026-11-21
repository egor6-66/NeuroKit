---
name: show-background-refresh
description: Keep the last result visible and show a local progress indicator while the same web-core query refreshes.
---

Use the result and fetch state from `@web-core/query` to decide what the user sees. During the first fetch, show a loading state until a result arrives. Show an empty list message only after a successful response with zero items. An initial failure needs an error state.

When the same query fetches again, keep its last successful result on screen. While `query.isFetching` is true, show a visible indicator beside the data it describes. For example, after an agent is renamed, keep the rows in place and show “Updating…” in the list header. Keep the indicator visible for the duration of the fetch. On success, render the updated result and clear the indicator. On failure, clear the indicator, keep the last result, and tell the user the refresh failed.

Verify with a slow refresh of a populated list. The rows and the indicator should be visible together while the request runs. Check both a successful response and a failed refresh.
