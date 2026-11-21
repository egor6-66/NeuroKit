---
name: build-entity-form
description: Build or change an entity action form in a Solid FSD application using web-core, including forms composed from multiple entities or submitted from an external control.
---

1. Trace the nearest form for a similar action. Read the relevant web-core form README and example, and check how the application renders a form model. In NeuroBoard, start with the entity's model, the matching feature, and the shared Form component.
2. For the requested action, reuse or extend the entity's field definitions and form model. Put field order, bindings, validation, dependent fields, and create or edit initial values there. Reuse registered field names for selectors supplied by other entities. Expose the needed model and action through the entity's public API.
3. In the feature, compose the form model with any other entities' forms, fields, or live data needed by the scenario. Pass choices, pending state, and errors into the form. Connect validated submission to the entity action. For example, NeuroBoard's CreateAgent uses agentCreateForm and agent.create, while AgentForm supplies choices for models, keys, and rules.
4. Review the form and its states before integrating it into the screen. The page places the feature and supplies screen-specific callbacks. In NeuroBoard the page can render <CreateAgent onDone={close} /> inside its dialog.
5. When a header button or keyboard shortcut also saves the form, route it through the same validated submit command. While its request is pending, the command must ignore another submission from any of those controls. Expose the command and its availability only when an external control needs them. NeuroBoard's EditAgent exposes form.submit and form.locked through bind.
6. Exercise the actual save path. With invalid input, validation should prevent the entity action from running. With valid input and a slow response, click Save and press Enter before the response arrives. Verify that only one request is sent. If the action fails, surface the error and keep the draft available. If there is an external save control, verify these outcomes through that control too.
