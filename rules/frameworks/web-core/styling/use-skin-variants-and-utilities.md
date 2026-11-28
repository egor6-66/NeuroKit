---
name: use-skin-variants-and-utilities
description: Define reusable component appearances as skin variants and apply small local adjustments with web-core skin utilities.
---

Choose a documented component variant for the intended appearance. When a component needs a distinct reusable look, define a named variant in the skin and select it through the component's variant API, such as data-variant. Define the variant by a reusable role of the component. For example, a destructive button can have the same appearance in a dialog and in a toolbar. Keep the account header's choice, order, and placement of actions in the header composition. If a proposed variant only makes sense for those particular actions in that spot, keep the existing component variant and compose the placement locally.

Before styling a composite component, check its documented anatomy in the component README. Target the part that owns the property through the skin. For a dialog with a fixed header and scrolling content, set the panel dimensions on `content` and scrolling on `body`. Use documented part names rather than positional DOM selectors such as `div:last-child`, whose target can change with the composition.

For a small adjustment specific to one placement, keep the base variant and use the inline style utilities from @web-core/skin. A difference in one layout setting, such as the gap between items in a single toolbar, is usually a local adjustment. If the adjustment expresses a reusable visual role, it can warrant a variant even when only one property changes.

Application markup uses component variants and the skin's documented styling utilities. Do not add CSS classes, utility class strings, or page stylesheets to reproduce a mockup. For a row of actions, compose the framework's Flow and Button components and select variants supplied by the active skin. The screen owns which actions appear and in what order.

Use skin utilities for a supported local adjustment. For example, layoutSelf places an element in its parent and layoutGroup arranges a container's children. Keep settings owned by a component's documented variant in that variant. Reserve raw inline CSS for exceptional cases where the required value cannot be expressed by the available utilities or token helpers. Keep such an exception scoped to the property that needs it.
