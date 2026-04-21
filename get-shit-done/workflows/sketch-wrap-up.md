<purpose>
Curate sketch findings. Persistent project skill. Summary generation.
</purpose>

<process>

S1: Intake
- Read `.planning/sketches/`. Identify variants selected.

S2: Extract
- Patterns, colors, spacing, HTML/CSS fragments.
- Tool: `gsd-sdk query extract-design-tokens`.

S3: Save Skill
- Dir: `.claude/skills/sketch-findings-[project]/`.
- Content: Implementation-ready prompt with visuals/code snippets.

S4: Summary
- `.planning/sketches/WRAP-UP-SUMMARY.md`.
- Next: `/gsd-plan-phase`.
</process>
