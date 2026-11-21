---
name: choose-state-ownership
description: Choose one owner for each component state, such as whether a dialog is open.
---

Use the component's built-in state when all interactions with that state are local. An option such as defaultOpen sets the initial state. When other parts of a scenario must control the component, use its supported controlled API or a shared controller at the level that coordinates those participants. Route changes through that owner. Mirroring the same state into a second signal introduces synchronization work for every way it can change.

For example, NeuroBoard's agents page owns a useModal controller. Navigation opens the creation dialog through that controller. The form reports successful completion through onDone, and the page supplies the close action. The form can be reused in another layout with a different completion action.

Verify each supported close path, such as the close button, Escape, and successful submission. After each one, the next open action should reopen the dialog on the first attempt.
