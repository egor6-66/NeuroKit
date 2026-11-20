---
name: compose-entity-forms-in-features
description: Keep action form definitions in entities, compose their behavior in features, and place ready-to-use features on pages.
---

An entity owns the form definitions for its actions. Describe its fields, their order and bindings, validation, dependencies, and initial values for creation or editing. Expose the definitions and operations consumers need through the entity's public API.

A feature implements the user action. Start from the entity's form definition. When the action spans entities, compose their forms, fields, and data through their public APIs. Connect live inputs and submission to the relevant entity operations. Keep cross-entity coordination in the feature so the participating entities remain independent.

A page composes the screen and supplies screen-specific behavior: where the feature appears, which record is selected, and whether completion closes a dialog or navigates elsewhere. Follow the same boundaries when the form has a single screen consumer.

For example, in NeuroBoard the agent entity exposes agentCreateForm and agentEditForm. The agent-form feature supplies model, key, and rule choices and connects the form to agent.create or agent.update. The page opens the creation dialog and renders <CreateAgent onDone={close} />.
