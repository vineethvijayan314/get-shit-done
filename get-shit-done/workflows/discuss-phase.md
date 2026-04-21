# Phase: Discuss
Trigger: `/gsd-discuss-phase [phase_number] [--auto]`

## S1: Alignment
- Agent: `gsd-advisor-researcher`.
- Goal: Clarify intent. Surface assumptions.
- Logic: `gsd-sdk query init.discuss-phase "$PHASE"`.

## S2: Research
- Agent: `gsd-advisor-researcher`.
- Action: Level 2 Discovery. `grep` + Web search.

## S3: Auto-Advance
- If `--auto`: Launch `gsd-plan-phase`.
- Prompt: "Context captured. Launching plan..."
