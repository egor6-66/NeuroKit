---
name: compose-documented-component-parts
description: Compose UI from the parts and behavior provided by web-core components.
---

For application markup, use the public web-core components for layout, surfaces, typography, and controls. For example, look up Flow for a row of actions, Grid for aligned columns, and Button for the action itself. A native wrapper or control duplicates the component when web-core already supplies that role. Read the component's README and its nearest usage example for the version the app uses. Identify the parts the caller supplies and the behavior the component already owns.

For example, supply the application's creation form as dialog content. Compose the documented dialog parts and reuse their focus handling, backdrop, and dismissal behavior. If the composition cannot support the interaction, identify the missing capability before introducing a custom implementation.
