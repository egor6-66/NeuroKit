---
name: compose-documented-component-parts
description: Compose UI from the parts and behavior provided by web-core components.
---

Before implementing a UI interaction, read the component's README and its nearest usage example. Identify the parts the caller supplies and the behavior the component already owns.

For example, supply the application's creation form as dialog content. Compose the documented dialog parts and reuse their focus handling, backdrop, and dismissal behavior. If the composition cannot support the interaction, identify the missing capability before introducing a custom implementation.
