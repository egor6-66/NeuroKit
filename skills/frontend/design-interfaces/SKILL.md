---
name: design-interfaces
description: Design and assess modern frontend interfaces. Use when creating a screen or component, choosing a visual direction, or refining the composition, typography, density, and responsive behavior of existing UI.
---

## Establish the visual direction

Start with the content someone will actually see and the decision or action the interface supports. For a new screen, sketch the reading order with realistic labels, values, and actions. Within an existing product, inspect related screens and its design system for conventions users already recognize. Use visual references for hierarchy, rhythm, and composition. Their markup and CSS belong to the reference project.

Give the screen a visual direction specific enough to guide a choice. A monitoring console might use closely spaced rows, aligned numbers, and a strong accent for exceptions. A collection of illustrations might lead with generous image areas and quiet captions. When the brief calls for a current trend, look at recent references for the same kind of product. Identify the particular choice worth borrowing and how it helps this audience.

## Translate the design into the project's UI

Before editing UI code, read the project's component and styling rules, the closest conforming screen, and the documented primitives for this layout. Map each visual role to an existing component and its public API, including layout, surfaces, headings, and controls. In a project that composes UI from a kit, use those components throughout. Start with the chosen composition and variant as supplied by the project's design system. Add a local style only when you can identify a requirement that this composition leaves unmet. Keep the built-in spacing when it already gives the intended hierarchy. Introducing native markup or CSS classes to reproduce a reference bypasses those contracts.

Keep a screen's arrangement in its composition. For a bento overview, the screen chooses which tile leads and how its contents are grouped. The shared surface can supply the same appearance wherever that surface is used. A new shared variant needs a component-level meaning that still holds on another screen. If the proposed design needs an unavailable capability, identify the gap and offer a composition the project supports. If extending the shared library would expand the task, agree on that change first.

## Choose a composition that fits the content

- A bento grid suits an overview with distinct kinds of content and a reason for their different sizes. A large active-project tile can show the next milestone and its action. A smaller tile can show the latest build. On a narrow screen, put the active project first and let the remaining tiles follow in reading order.
- For repeated records people compare, align the same attributes down a list or table. On a build-history screen, consistent columns for revision, status, and duration let someone scan for a slow run. Give detail on demand to the run they select.
- For a sequential task such as configuring a deployment, group related inputs in reading order, keep descriptions beside the fields they explain, and place the next action where that group ends.

## Make the hierarchy visible

Choose what the eye should land on first. Establish that focal point with placement, scale, or contrast. Give titles, body text, and metadata distinct, repeatable type roles. Use a common alignment edge and make the space within a group smaller than the space between groups. Add a surface or divider where it clarifies a boundary.

Use color consistently for emphasis and status. Pair a status color with a readable label or recognizable symbol. Choose imagery, depth, and motion for a specific purpose. For example, a brief transition can show where an expanded panel came from. Keep that relationship legible with reduced motion.

## Check the rendered result

For implemented UI, inspect the changed markup and styles for hand-built substitutes, ad hoc classes, and shared variants tied to a single placement. Resolve each mismatch against the project rules. When a preview is available, inspect it at wide and narrow widths with realistic content, including a long label or a crowded row. Check where attention lands, whether the primary action remains visible and reachable, and whether reading and keyboard focus follow a sensible order. Inspect text contrast and visible focus in the actual colors. For a design-only proposal, show the composition with representative content and explain the choice that most affects the user's task.
