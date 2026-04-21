# GSD Model Profile Resolution

Determine which model profile to use.

## Rules
1. Check `PROJECT.md` for explicit model preference.
2. IF unknown -> Default to `reasoning` for plans, `velocity` for execution.
3. IF tool failure -> Downgrade to `velocity`.

## Mapping
- `gsd-planner` -> reasoning.
- `gsd-executor` -> velocity.
- `gsd-debugger` -> reasoning.
