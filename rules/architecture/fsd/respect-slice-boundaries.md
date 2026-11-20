---
name: respect-slice-boundaries
description: Import across slice boundaries only from strictly lower FSD layers, through their public APIs.
---

Within a slice, its segments may use one another's modules. Across slice boundaries, import only the public API of a slice on a strictly lower layer. This applies to every layer with slices, to type-only imports, and to re-exports. The team does not use the FSD @x exception for cross-entity imports.

For example, features/move-agent can use entities/agent and entities/project. An entity cannot import that feature, entities/agent cannot import entities/project, and features/move-agent cannot import a sibling feature. The same rule applies between sibling widgets or sibling pages.

Put composition on the layer that owns the scenario. A page showing an agent and its project name can consume both entities. A reusable presentation block can compose them in a widget. A user action that moves the agent can coordinate their operations in a feature. Avoid moving domain-specific composition into shared just to make an import point downwards.

[FSD — Layers and the import rule](https://feature-sliced.design/docs/reference)
