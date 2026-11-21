---
name: derive-selection-from-route
description: Use a route parameter as the source of truth for a selection that users can open by URL.
---

When a link should open a particular item or tab, read the selection from the route on every render. A user selection navigates to the corresponding URL. A second signal updated by the click handler can fall out of sync when the user follows a link or presses Back. Keep transient interactions such as hovering over a row local to the component.

For an agent list at `/agents/$id`, use `useRouteParamSelection("id", "/agents/$id")` from `@web-core/router`. Read `selection.value` reactively for both the highlighted row and the displayed agent. When the user picks a row, call `selection.select(id)`. If the route defines a default selection, pass it as `defaultValue`. The helper fills a missing parameter by replacing the current history entry and preserves an explicit value from a link.

Verify the whole interaction. Open a direct link to agent A, select B, press Back, then reload. The URL, highlighted row, and detail panel should agree at each step.
