---
name: verify-scenario-end-to-end
description: Verify a specific scenario from its triggering event to its observable outcome in one run.
---

Identify the triggering event, the conditions that matter, and the observable outcome that marks success.
Run the complete scenario under those conditions. Follow the same execution from the trigger through every handoff to the expected outcome.
Use component checks to locate failures. Even when each component passes in isolation, verify that data and control flow correctly between them in the complete run.
If a full run is unavailable, report which part of the scenario was verified and which transitions or outcomes still need verification.

For example, to verify a scheduled agent run, let the timer fire and observe the resulting agent run complete. Calling the launch function directly only verifies behavior downstream of that call.
