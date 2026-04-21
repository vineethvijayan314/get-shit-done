# GSD Model Profiles

Calibration per LLM capability.

## Profile: reasoning (Sonnet 3.5, O1)
- Complexity: High.
- Research: Deep.
- Planning: Multi-phase.
- Role: `gsd-planner`, `gsd-debugger`.

## Profile: velocity (Sonnet 3.5, GPT-4o)
- Complexity: Medium.
- Research: Fast.
- Logic: Direct.
- Role: `gsd-executor`, `gsd-code-fixer`.

## Calibration logic
1. Read `MODEL-PROFILE.json`.
2. Sync agent logic (Self-correction count, Research depth) to profile type.
