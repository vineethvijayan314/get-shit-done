<purpose>
Start new milestone cycle. Update PROJECT/STATE. Scoped requirements -> Roadmap. Archival check.
</purpose>

<process>

S1: Load Context
- Parse `$ARGUMENTS`: `--reset-phase-numbers`, `${MILESTONE_NAME}`.
- Read: PROJECT.md, MILESTONES.md (archived versions), STATE.md.
- Check: `MILESTONE-CONTEXT.md` (from discuss).

S2: Milestone Goals
- Found context -> Use features + scope.
- No context -> Ask: "What do you want to build next?"

S2.5: Seed Sync
- Check `.planning/seeds/SEED-*.md`.
- Match seed triggers against goals.
- Selection choice: Include in scope | Skip.

S3: Versioning
- Parse last version. Suggest next (v1.0 -> v1.1).
- Confirmation summary.

S4: Update PROJECT.md
- Inject `Current Milestone` header.
- List target features.
- Ensure `## Evolution` section exists.

S5: Initialization
- `INIT=$(gsd-sdk query init.new-milestone)`.
- Agents: `project-researcher`, `synthesizer`, `roadmapper`.
- Archive old phases if `--reset-phase-numbers` + `phase_dir_count > 0`.

S6: Research Choice
- Prompt: "Research domain for new features?".
- Action (if yes): Parallel 4x `gsd-project-researcher` -> `gsd-research-synthesizer`.
- Commit `SUMMARY.md`.

S7: Scope Requirements
- Categories: FEATURES.md + Seeds + Discussion.
- Selection choice: This milestone | Future | Out of scope.
- Generate `REQUIREMENTS.md`. Mapped REQ-IDs. Traceability section (empty).

S8: Roadmap Generation
- Spawn `gsd-roadmapper`.
- Rules: Map every REQ-ID to 1 phase. derive success criteria.
- Phase Numbering: Start at 1 (reset) OR continue (default).
- Write: ROADMAP.md, STATE.md, update REQUIREMENTS.md.
- Commit all.

S9: Wrap
- Output: Artifact map + Next phase ready.
</process>

<success_criteria>
- [ ] PROJECT.md updated with Current Milestone.
- [ ] REQUIREMENTS.md mapped with REQ-IDs.
- [ ] ROADMAP covers all milestone requirements.
- [ ] Phase numbering respected.
</success_criteria>
