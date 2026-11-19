---
name: preserve-user-data
description: Preserve existing user data when changing its format or storage location.
---

Check how the change affects both a fresh installation and an upgrade with existing data.
When old and new representations coexist, determine which values the user has changed. Preserve those values when merging. If a conflict cannot be resolved safely, retain both versions and report the conflict.
Run the upgrade on representative existing data, change a migrated value as a user would, and run the upgrade again. Verify that the value survives and that the operation can be retried after a partial migration.

For example, when adding an agent setting, verify that a new agent gets the default, an existing agent can load without the field, and reopening the agent preserves the user's chosen value.
