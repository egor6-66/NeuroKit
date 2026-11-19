---
name: avoid-hardcoded-assumptions
description: Resolve values that vary across projects, users, or machines from their existing source.
---

Before hardcoding a name, address, path, or model, check who chooses it and where the application already gets it.
Read project-specific values from the project configuration, user-specific values from the selected account or preferences, and runtime values from the current environment or state.
Reuse the existing source when one is available. Keep fixed values in code when they are part of the contract across all supported cases.

For example, when authenticating a Git push, use the destination host of the selected remote. A self-hosted GitLab project must work with its configured host.
