---
name: scope-reactive-cleanup
description: Release subscriptions, timers, and event listeners when their owning Solid scope ends or refreshes.
---

Identify when the resource should stop acting. Register cleanup next to setup, in the Solid scope that owns that resource. For a component-lifetime timer, register clearInterval when creating the interval in onMount. For a subscription keyed by a reactive prop, create the subscription and register its disposer inside the same effect.

```tsx
createEffect(() => {
  const unsubscribe = agentEvents.subscribe(props.agentId, handleEvent)
  onCleanup(unsubscribe)
})
```

Here subscribe returns a function that releases this particular subscription. When agentId changes, Solid disposes the old subscription before the effect subscribes to the new agent. Unmounting the panel disposes the current subscription.

Verify both transitions. Switch from agent A to B while the panel stays mounted and check that only B's events reach it. Then close the panel and check that it receives no further events.

[Solid — onCleanup](https://docs.solidjs.com/reference/lifecycle/on-cleanup)
