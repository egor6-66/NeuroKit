---
name: reuse-existing-logic
description: Check existing solutions against current project rules before reusing or extending them.
---

Before adding logic, find how the project already handles the same case.
If both workflows should behave the same way and the implementation follows the current project rules, reuse it.
If that logic is embedded in one workflow, extract the shared part and call it from both.
Keep the steps specific to each workflow where they belong.

Before reusing code or following its pattern elsewhere, check it against the current project rules. If the code conflicts with a rule, follow the rule. Point to the file and line or symbol, name the rule, and explain the conflict. Do not copy that pattern or build new logic on it.

If you can complete the task within the agreed scope while following the rules, proceed. If doing so requires changing existing code outside that scope, explain why the task depends on that change and agree on the scope with the user before making the change.
