---
name: use-links-for-navigation
description: Use a router link for direct navigation and navigate after an action succeeds when the workflow calls for it.
---

When a control takes the user directly to a known route, render a `Link` from `@web-core/router`. For example, the name of an agent in a list can link to its detail page:

```tsx
<Link to="/agents/$id" params={{ id: agent.id }}>{agent.name}</Link>
```

When the user submits a form to create an agent, keep the submit button. If the workflow opens the created agent, use `useNavigate()` from `@web-core/router` and call `navigate({ to: "/agents/$id", params: { id: created.id } })` after creation succeeds. On failure, keep the form open with the user's input and show the error.

Verify that the agent link opens the same detail page through a normal click, in a new tab, and from its copied address.
