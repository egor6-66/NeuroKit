---
name: use-skin-variants-and-utilities
description: Define reusable component appearances as skin variants and apply small local adjustments with web-core skin utilities.
---

Choose a documented component variant for the intended appearance. When a component needs a distinct reusable look, define a named variant in the skin and select it through the component's variant API, such as data-variant. Keep the styling shared by consumers in that variant.

For a small adjustment specific to one placement, keep the base variant and use the inline style utilities from @web-core/skin. A difference in one layout setting, such as the gap between items in a single toolbar, is usually a local adjustment. If the adjustment expresses a reusable visual role, it can warrant a variant even when only one property changes.

Use skin utilities for inline styles by default. Use layoutGroup for how a container arranges its children, layoutSelf for an item's placement in its parent, and the matching token helper for individual dimensions. For example:

```tsx
import { layoutGroup } from "@web-core/skin"

<div style={layoutGroup({ gap: "space-4" })}>
  <Button data-variant="danger">Delete</Button>
</div>
```

Here the skin owns the destructive button appearance and the container owns its local gap. Reserve raw inline CSS for exceptional cases where the required value cannot be expressed by the available utilities or token helpers. Keep such an exception scoped to the property that needs it.
