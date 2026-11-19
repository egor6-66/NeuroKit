---
name: reuse-existing-logic
description: Reuse existing behavior when adding a new workflow.
---

Before adding logic, find how the project already handles the same case.
If both workflows should behave the same way, reuse the existing implementation.
If that logic is embedded in one workflow, extract the shared part and call it from both.
Keep the steps specific to each workflow where they belong.
