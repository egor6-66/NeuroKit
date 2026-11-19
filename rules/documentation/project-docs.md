---
name: project-docs
description: Choose the project document that answers the reader's question.
---

Use the project's existing document names and formats.

- README describes the project as it works today. Explain its purpose, main entities and relationships, features, and settings. Link to detailed procedures in docs/ when relevant.
- FAQ explains decisions that genuinely raise questions, including custom behavior, surprising constraints, and deliberate exceptions. If code is hard to follow, first clarify its names, steps, or responsibilities. Put any remaining rationale in the FAQ. Avoid explanatory comments or FAQ entries that merely restate what the code does.
- ROADMAP shows agreed future work, including deferred bugs and planned features. Record what needs to change and why. Add an item when the team decides to defer or plan the work. Remove completed items and keep implementation diaries out of the plan.
- docs/ contains procedures and conventions such as server setup, deployment, code style, and architecture. Reuse guidance shared by projects on the same stack and identify project-specific differences where they affect the procedure.

After feature acceptance, update the documents whose answers have changed. Record explicitly agreed future work in the roadmap during planning.
