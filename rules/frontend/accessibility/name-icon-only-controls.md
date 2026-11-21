---
name: name-icon-only-controls
description: Give icon-only buttons and links an accessible name that identifies their action or destination.
---

Give the interactive element a name in the language of the interface. Use its visible text when that text already explains its purpose. For an icon-only control, put the label on the button or link itself, for example with `aria-label`. Hide a purely decorative icon from assistive technology.

When the same action appears in several rows, include the item in the name so each control makes sense on its own. For a pencil button in the Atlas agent row, use “Edit agent Atlas”. For a link to that agent's run history, use “Run history for Atlas”.

Check the controls in the browser's accessibility tree. Each should expose its button or link role and a name that tells the user what selecting it will do, even when navigating through the controls without reading the surrounding rows.
