---
name: work-in-reviewable-steps
description: Give the user a review point before building on each implementation decision.
---

Split even a narrowly scoped feature into steps when it involves decisions the user can review independently. Briefly outline the sequence. For the next step, state its outcome, the affected areas, and why they need to change. A specific request can already authorize a single step.
Implement only the agreed step. If it would require changes across many files or outside the agreed area, pause before making those changes. Explain the dependency and revisit the design, scope, or task interpretation with the user.
After each step, briefly state what is ready and how it was checked. End every work pass that changes files with a plain list of the paths you changed in that pass. Use one repository-relative path per line, with no descriptions. Include files you created, edited, renamed, or deleted. Wait for the user's acceptance before starting the next step. Address feedback within the current step.
Use existing checks or a manual demonstration during implementation. Verify the complete feature at integration. Write new tests and documentation only after the user accepts the functionality of the whole task.

For example, a frontend agent-creation feature may need an entity, an API call, a form, and screen integration. Reuse an existing entity if it fits. Review each new piece before building on it, and let the user review the form and its states before integrating it into the screen.
