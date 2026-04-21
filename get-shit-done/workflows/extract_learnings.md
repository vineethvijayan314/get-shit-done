<purpose>
Extract decisions/lessons/patterns/surprises from completed phase artifacts. Institutional memory capture.
</purpose>

<process>

S1: Setup
- Resolve phase: `PHASE_ARG` -> `padded_phase`.
- Required: PLAN.md, SUMMARY.md.
- Optional: VERIFICATION.md, UAT.md, STATE.md.

S2: Analyze
- **Decisions**: Choices + rationale. Source: PLAN/SUMMARY.
- **Lessons**: Unexpected findings + context. Source: SUMMARY/VERIFICATION.
- **Patterns**: Reusable techniques + applicability. Source: SUMMARY.
- **Surprises**: Behavior vs expectation + impact. Source: SUMMARY.

S3: Capture
- If `capture_thought` available -> send all 4 categories with metadata.

S4: Write
- File: `${PHASE_DIR}/${PADDED_PHASE}-LEARNINGS.md`.
- YAML frontend: phase, name, project, counts, missing_artifacts.
- Body: 1 section per category + source attribution.

S5: Wrap
- Update STATE.md timestamp. Report counts to user.
</process>
