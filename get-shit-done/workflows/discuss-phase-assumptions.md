<purpose>
Assumption-led discovery. Codebase-first analysis.Surfaces misconceptions early. Think-partner flow.
</purpose>

<process>

S1: Setup
- Resolve `PHASE`. Load `roadmap`, `state`, `manifest`.
- Calibration: `USER-PROFILE.md` -> thorough | opinionated | standard.

S2: Analyze
- Spawn `gsd-assumptions-analyzer`.
- Logic: Read ROADMAP description vs existing code patterns.
- Output: Structured assumptions (Area, Statement, Evidence [files], Consequence, Confidence).

S3: Research
- IF topics flagged as external -> spawn `general-purpose` subagent.
- Resolve version/compatibility ambiguities. Update confidence.

S4: UI Gate
- Format: Area + Confidence Badge + Statement + Evidence + Consequence.
- IF Confident -> Proceed.
- IF Unclear -> `AskUserQuestion`. Resolved via Alternatives.

S5: Write
- `.planning/phases/NN-*/NN-CONTEXT.md`. Standard sections.
- `.planning/phases/NN-*/NN-DISCUSSION-LOG.md`. Audit trail.

S6: Finalize
- Commit report. Next: `/gsd-plan-phase`.
</process>
