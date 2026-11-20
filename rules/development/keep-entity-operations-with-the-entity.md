---
name: keep-entity-operations-with-the-entity
description: Give each entity one module that owns its operations and let consumers compose them into workflows.
---

Implement operations on an entity in its owning module. Expose the operations callers need through that module's public interface, including lookup, creation, and changes. When a workflow needs a missing operation, add it to the owning module. Keep each operation focused; the module may organize its implementation across several files.
Keep lookup mechanics, storage details, and entity-specific validation inside the module. Give callers an explicit result when an entity is missing or a change is rejected. A consumer supplies input, sequences operations, and decides how its workflow responds to their outcomes.

For example, a form calls agents.rename(id, name). The agents module looks up the agent, validates the name, persists the change, and reports the outcome. The form closes on success or displays an error. A CLI can reuse the same rename operation and handle the outcome in its own way.
