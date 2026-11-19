---
name: fix-at-the-source
description: Trace a defect to the code responsible for the expected behavior.
---

Establish the expected behavior and trace the failing case to the first point where it diverges.
Fix the code responsible for that behavior. If the input is valid, check the assumptions made by the code consuming it.
Verify the fix through the workflow where the defect was observed.
If earlier failures left invalid data behind, determine how to handle those records separately.
