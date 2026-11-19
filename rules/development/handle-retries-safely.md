---
name: handle-retries-safely
description: Preserve the intended effect when a caller retries a state-changing operation.
---

For each state-changing operation, determine whether its caller may retry after a timeout or failure.
Where a retry could duplicate the effect, define how to recognize the same logical request across attempts while allowing an intentional new action with identical inputs.
Verify the case where the change has already taken effect but the caller missed the acknowledgement. Retrying must preserve the original effect. A separate intentional request must still succeed.

For example, a scheduler can assign one request ID per scheduled run and reuse it on every delivery attempt for that run. When NeuroBox receives the same ID again, it returns the existing run. The next scheduled run gets its own ID even if the agent and prompt are identical.
