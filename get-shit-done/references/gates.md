# GSD Gates

System validation checkpoints.

## Types

| Name | Role | Location |
|------|------|----------|
| **Setup Gate** | Verify init state. | `new-project` |
| **Context Gate** | Lock decisions. | `discuss-phase` |
| **Logic Gate** | Verify commit. | `execute-phase` |
| **Ship Gate** | Release audit. | `ship` |

## Control
- IF gate FAIL -> Stop workflow.
- IF gate PASS -> Advance to NEXT step.
