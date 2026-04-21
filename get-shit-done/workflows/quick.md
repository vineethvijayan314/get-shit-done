# Phase: Quick Task
Trigger: `/gsd-quick [description] [--validate] [--discuss] [--research]`

## S1: Init
- Logic: `slug=$(echo $DESC | slugify)`. `id=$(gsd-sdk query id.next-quick)`.
- Dir: `.planning/quick/${id}-${slug}/`.

## S2: Discuss (optional)
- Agent: `gsd-advisor-researcher`.
- Goal: Align intent. Cite D-XX.

## S3: Research (optional)
- Agent: `gsd-advisor-researcher`.
- Action: Discovery level 2.

## S4: Execute
- Agent: `gsd-executor`.
- Process: Atomic commit. Deviations allowed.

## S5: Review (optional)
- Agent: `gsd-code-reviewer`.
- Logic: Adversarial review of diffs.

## S6: Verify (optional)
- Agent: `gsd-verifier`.
- Logic: Goal-backward check.

## S7: State
- Update: `STATE.md` Quick Tasks table.
