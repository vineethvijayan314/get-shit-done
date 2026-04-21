# Phase: New Milestone
Trigger: `/gsd-new-milestone [name]`

## S1: Init
- Logic: `gsd-sdk query init.new-milestone "$NAME"`.
- Action: Create `PROJECT.md`, `ROADMAP.md` updates.

## S2: Milestone Plan
- Agent: `gsd-roadmapper`.
- Output: Milestone specific roadmap phase.
