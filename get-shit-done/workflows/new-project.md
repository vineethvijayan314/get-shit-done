# Phase: New Project
Trigger: `/gsd-new-project`

## S1: Setup
- Logic: `gsd-sdk query init.new-project`.
- Action: Create `.planning/` structure.

## S2: Definition
- Agent: `gsd-roadmapper`.
- Output: `PROJECT.md`, `REQUIREMENTS.md`, `STATE.md`, `CONVENTIONS.md`.

## S3: Skill Discovery
- Action: Run `@gsd-build/skill-discovery`.
