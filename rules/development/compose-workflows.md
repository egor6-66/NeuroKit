---
name: compose-workflows
description: Build workflows from meaningful operations and let each caller handle their outcomes.
---

When a feature has clear steps with distinct responsibilities, define those operations from the start, even if only one workflow uses them today.
Give each operation explicit inputs, a meaningful outcome, and a clear way to report failure.
Let the calling workflow choose the operations, their order, and how to handle each outcome. Keep caller-specific decisions such as displaying a message or scheduling a retry in that workflow.

For example, creating an agent returns its ID. A create-and-run workflow passes that ID to the launch operation. Manual and scheduled runs can call the same launch operation with an existing ID. If launch fails after creation succeeds, the caller can report or retry the launch using that ID.
