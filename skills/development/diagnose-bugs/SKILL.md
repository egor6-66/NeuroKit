---
name: diagnose-bugs
description: Diagnose a reported bug by reproducing the failing scenario, locating the first incorrect result, and testing the suspected cause before changing behavior.
---

1. Establish what failed. Identify the entry point, affected record or input, relevant state, and action. Write down the expected and observed results. Try the reported path on the project's shared instance. If the failure is intermittent, capture the conditions of a failing run and compare them with a successful run. If it remains inaccessible, report what you observed and what evidence is still needed.
2. Follow the same failing case across the relevant boundaries. Use existing observations such as the request and response, a returned value, component props, or the rendered output. Locate the last correct value and the first incorrect one. A nearby working case can help isolate the difference.
3. State a hypothesis and a prediction that would distinguish it from another plausible cause. Check that prediction with a focused observation. If it fails, revise the hypothesis before editing. Finding a branch that *could* produce the symptom gives you a place to inspect.
4. For a diagnosis request, report the cause and the observation that establishes it. When a fix is requested, change the owner of the incorrect behavior within the agreed scope. Repeat the original action with the same input and state. Report the observed outcome and any remaining gap in verification.

For example, if an archive action is missing for one editable document, inspect that document's permission in the response, the operation's availability, the actions passed to the detail view, and the rendered control. If the view received the archive action, investigate how the view displays it. If the action was already missing on entry, trace back to the code that built it. After a fix, check the affected document again and confirm that a read-only document still follows its own permissions.

[Further reading — Systematic Debugging](https://github.com/obra/superpowers/blob/main/skills/systematic-debugging/SKILL.md)
