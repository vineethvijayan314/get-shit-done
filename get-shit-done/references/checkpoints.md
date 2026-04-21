# GSD Checkpoints

Control agent autonomy. Feedback gates. Safety protocols.

## Core Objective
Stop agent at critical logic/state changes. Require user verification. Prevent massive rollback cost.

## Checkpoint Types

| Type | Name | Trigger |
|------|------|---------|
| `auto` | Automatic | Task completion. Syntax check. |
| `review` | Peer Review | Code logic finish. BEFORE commit. |
| `intent` | Change Intent | Major deviation from plan found. |
| `safety` | Destructive | Deleting files. Resetting git. |

## Definition (PLAN.md)
```markdown
- [ ] type="checkpoint:review" title="Review Core Logic"
```

## Logic
1. Reached `checkpoint:*`?
2. Freeze state.
3. Show progress + diff.
4. `AskUserQuestion` (options: [Approve, Iteration, Cancel]).
5. IF Approve -> Proceed. IF Iteration -> update plan.
