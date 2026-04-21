<purpose>
Init new project. questioning -> research -> requirements -> roadmap. Idea to build-ready.
</purpose>

<process>

S1: Setup
- `INIT=$(gsd-sdk query init.new-project)`.
- Agents: `project-researcher`, `synthesizer`, `roadmapper`.
- Runtime check: set `$INSTRUCTION_FILE` (CLAUDE.md | AGENTS.md).
- Guard: `project_exists == true` -> Exit.

S2: Brownfield/Auto
- If `--auto`: Skip to S2a.
- If existing code: Offer `/gsd-map-codebase`.
- If Spike/Sketch skills exist: Read + Surface findings.

S2a: Auto Config
- Prompt Core: Granularity, Execution, Git.
- Prompt Agents: Research, Plan Check, Verifier, Models.
- `gsd-sdk query config-new-project {JSON}`.
- Commit `config.json`.

S3: Questioning
- Ask: "What do you want to build?"
- Loop: Socratic follow-ups. Challenge vagueness. Concrete examples.
- Gate: "Create PROJECT.md" approved.

S4: Write PROJECT.md
- Template: `templates/project.md`.
- Greenfield: Init requirements as hypotheses (Active).
- Brownfield: Infer Validated from map.
- Inject: Key Decisions, Evolution rules.
- `gsd-sdk query commit "docs: initialize project" .planning/PROJECT.md`.

S5: Workflow Preferences
- Check `~/.gsd/defaults.json`.
- Choice: Use defaults | Modify | Fresh.
- Multi-repo check: `gsd-workstreams` detection.

S6: Research
- Default: Research first.
- Actions: Spawn 4 parallel `gsd-project-researcher`.
- Dimensions: Stack (STACK.md), Features (FEATURES.md), Architecture (ARCHITECTURE.md), Pitfalls (PITFALLS.md).
- Sync: Spawn `gsd-research-synthesizer` -> SUMMARY.md.

S7: Define Requirements
- Source: FEATURES.md + Seeds + Conversation.
- Scoping Choice: Selected (In scope) | Unselected (Future/Out).
- Write `REQUIREMENTS.md`. Grouped by CATEGORY-ID.
- `gsd-sdk query commit "docs: define requirements" .planning/REQUIREMENTS.md`.

S8: Create Roadmap
- Spawn `gsd-roadmapper`.
- Logic: Map every REQ-ID to exactly one phase. Derive success criteria.
- Write: ROADMAP.md, STATE.md, update REQUIREMENTS.md.
- Commit all.

S9: Wrap
- Output: Artifact map + Scores.
- Next: `/gsd-discuss-phase 1`.
</process>

<success_criteria>
- [ ] PROJECT.md, config.json, REQUIREMENTS.md, ROADMAP.md created.
- [ ] Requirements testable + ID mapped.
- [ ] Roadmap covers 100% requirements.
- [ ] Atomic commits for each stage.
</success_criteria>
