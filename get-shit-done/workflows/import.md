<purpose>
Import external plan. Detect conflicts. Convert to GSD PLAN.md. Validate.
</purpose>

<process>

S1: Setup
- Parse `--from <path>`. Validate file exists.
- In-progress note: `--prd` mode TBD.

S2: Context
- Load: ROADMAP.md (structure), PROJECT.md (constraints), REQUIREMENTS.md (overlap), CONTEXT.md (decisions).

S3: Conflict Detection
- Blocker: Wrong phase, tech contradiction, decision defiance. Result -> Exit.
- Warning: Requirement overlap, dep lag, file collision. Result -> AskUserQuestion.
- Engine: `references/doc-conflict-engine.md`.

S4: Convert
- Logic: Map source tasks -> GSD YAML frontmatter.
- Naming: `{NN}-{MM}-PLAN.md` (MUST). No `plan-01` format allowed.
- Path: `.planning/phases/{NN}-{slug}/`.

S5: Validate
- Delegate: `gsd-plan-checker` subagent.
- Error -> Display + user fix. Success -> Proceed.

S6: Finalize
- Update ROADMAP.md sections.
- Update STATE.md counts.
- Commit: `docs({phase}): import plan from {file}`.
</process>
