---
name: respect-slice-boundaries
description: Import across slice boundaries only from strictly lower FSD layers, through their public APIs.
---

Within a slice, its segments may use one another's modules. Across slice boundaries, import only the public API of a slice on a strictly lower layer. This applies to every layer with slices, to type-only imports, and to re-exports. The team does not use the FSD @x exception for cross-entity imports.

For example, features/move-agent can use entities/agent and entities/project. An entity cannot import that feature, entities/agent cannot import entities/project, and features/move-agent cannot import a sibling feature. The same rule applies between sibling widgets or sibling pages.

Put composition on the layer that owns the scenario. A page showing an agent and its project name can consume both entities. A reusable presentation block can compose them in a widget. A user action that moves the agent can coordinate their operations in a feature. Avoid moving domain-specific composition into shared just to make an import point downwards.

When a lower-layer component owns the layout and a higher layer owns the content for one region, compose them at a layer that can import both. Accept children or a named slot for ready-to-render content. Use a render function when the content needs data or commands from the layout component. For example, NeuroBoard's agent page supplies EditAgent through the form slot of Agent.Details. The card passes its mode and callbacks to the slot, and the feature handles editing.

[FSD — Layers and the import rule](https://feature-sliced.design/docs/reference)
