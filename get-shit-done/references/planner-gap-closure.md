# GSD Planner Gap Closure

Detect missing context in plans.

## Objective
Find gaps between PRD requirements and PLAN tasks.

## Rules
- Task N+1 must start from state of Task N.
- All technical blockers identified in CONTEXT.md must have a specific Task for resolution.
- Reference missing? Flag Blocker.

## Process
1. Run `gsd-plan-checker`.
2. Map TASK objective vs CONTEXT decisions.
3. IF Gap > 0 -> Insert `fix: gap closure` task.
