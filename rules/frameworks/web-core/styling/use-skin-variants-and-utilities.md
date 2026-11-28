---
name: use-skin-variants-and-utilities
description: Use the active skin's component variants as supplied. Add a local style only for a specific layout requirement the existing composition does not meet.
---

Choose the simplest documented composition that meets the task with the active skin. For a vertical sequence, if the skin's column Flow already gives the requested result, the complete layout is:

```tsx
<Flow data-variant="column">{children}</Flow>
```

Baseline padding, gaps, and alignment belong to the skin. Writing a spacing token or calling a layout helper inline still overrides the skin. A simple column calls for no extra grid tracks, positioning, or sizing unless the content has a specific requirement for them.

When a component needs a distinct reusable look, define a named variant in the skin and select it through the component's variant API, such as data-variant. Define the variant by a reusable role of the component. For example, a destructive button can have the same appearance in a dialog and in a toolbar. Keep the account header's choice, order, and placement of actions in the header composition. If a proposed variant only makes sense for those particular actions in that spot, keep the existing component variant and compose the placement locally.

Before styling a composite component, check its documented anatomy in the component README. Target the part that owns the property through the skin. For a dialog with a fixed header and scrolling content, set the panel dimensions on `content` and scrolling on `body`. Use documented part names rather than positional DOM selectors such as `div:last-child`, whose target can change with the composition.

Before adding an inline declaration, identify what would be wrong in this placement with the variant alone. Check the composition and available variants first. If a real instance-specific difference remains, apply only the property it requires. For example, a user-resized pane may need its current measured width when the component exposes no size input. When reviewing an override, remove it and check the relevant state. If the layout still meets the requirement, leave it out.

Application markup uses component variants and the skin's documented styling utilities. Do not add CSS classes, utility class strings, or page stylesheets to reproduce a mockup. For a row of actions, compose the framework's Flow and Button components and select variants supplied by the active skin. The screen owns which actions appear and in what order.

For a justified override, use the documented @web-core/skin utility when it supports the property. For example, layoutSelf places an element in its parent and layoutGroup arranges a container's children. Keep settings owned by a component's documented variant in that variant. Reserve raw inline CSS for exceptional cases where the required value cannot be expressed by the available utilities or token helpers. Keep such an exception scoped to the property that needs it.
