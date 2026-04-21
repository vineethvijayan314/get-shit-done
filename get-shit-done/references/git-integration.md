# GSD Git Integration

VCS protocol. Atomic commits. Clean history. Conventional format.

## Core Rules
- NO `git reset`. Use `git revert --no-commit`.
- NO forced pushing.
- Commit per TASK completion.

## Commit Formats

| Type | Format |
|------|--------|
| **Planning** | `docs(plan): [phase] [desc]` |
| **Context** | `docs(context): [phase] [desc]` |
| **Logic** | `fix([phase]): [id] [desc]` |
| **New** | `feat([phase]): [id] [desc]` |
| **Revert** | `revert: [original commit msg]` |

## Rollback Protocol
1. Tool failure or user REJECT.
2. `git revert --no-commit [hash]`.
3. Clear working directory.
4. Update STATE.md.
