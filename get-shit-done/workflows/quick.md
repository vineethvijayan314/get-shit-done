<purpose>
Ad-hoc task execution. Single-command agility. GSD guarantees (atomic commits, STATE tracking).
</purpose>

<process>

S1: Setup
- Strip flags: `--full` (quality pipeline) | `--no-commit`.
- Check `.planning/quick/` DIR. Create if missing.

S2: Plan
- Spawn `gsd-planner` (mode: quick).
- Result: Micro-plan in `.planning/quick/TASK-ID.md`.
- IF `--full` -> Add `gsd-research-phase` + `gsd-verify-work`.

S3: Execute
- Spawn `gsd-executor`.
- Constraints: Target only files in micro-plan. No scope creep.

S4: Verify
- Default: Syntax + build.
- IF `--full` -> Run `gsd-verify-work`.

S5: Commit
- Logic: Atomic commit logic (convention).
- Update: `STATE.md` quick tasks table.
</process>
