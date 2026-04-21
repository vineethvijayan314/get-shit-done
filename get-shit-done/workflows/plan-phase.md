<purpose>
Create executable phase prompts (PLAN.md). Orchestrate research -> planning -> verification. Integrate design/security/schema gates.
</purpose>

<process>

S1: Initialize
- Parse Args: `${PHASE}`, flags (`--research`, `--gaps`, `--prd`, `--reviews`, `--bounce`).
- `gsd-sdk query init.plan-phase`.
- Load configs: `TDD_MODE`, `CONTEXT_WINDOW` (1M enrichment), `DISCUSS_MODE`.

S2: PRD Express Path
- Trigger: `--prd <file>`.
- Logic: Bypasses interactive discussion.
- Action: Parse PRD -> Extract requirements -> Map decisions -> Create CONTEXT.md -> Commit.

S3: Context Gate
- Check `context_path`. If missing:
  - Assuptions mode -> `gsd-discuss-phase-assumptions`.
  - Discuss mode -> `gsd-discuss-phase`.
- REQ: User MUST run discuss-phase if context missing. Stop here unless `--auto`.

S4: AI Integration Gate
- Check: AI keywords in goal + `workflow.ai_integration_phase`.
- Guard: If AI detected & no AI-SPEC -> Stop & suggest `/gsd-ai-integration-phase`.

S5: Research Loop
- Skip: `--gaps`, `--skip-research`, `--reviews`.
- Trigger: MISSING RESEARCH.md or `--research`.
- Task(gsd-phase-researcher): Answer "What do I need to know to PLAN well?".
- Output: `*-RESEARCH.md`.

S6: Validation Strategy (Nyquist)
- Trigger: `research_enabled` + `nyquist_validation_enabled`.
- Logic: Read "Validation Architecture" from Research -> Fill `*-VALIDATION.md` template.

S7: Safety Gates
- **Security**: ASVS Level check. REQ: `<threat_model>` in plans.
- **UI**: Check goal for frontend indicators. REQ: `*-UI-SPEC.md`. If missing -> `/gsd-ui-phase`.
- **Schema**: Scan for Prisma/Drizzle/Supabase/Payload patterns.
- REQ: Inject `[BLOCKING]` schema push task if detected.

S8: Pattern Mapping
- Trigger: `workflow.pattern_mapper: true`.
- Task(gsd-pattern-mapper): Extract analogs/excerpts from Research/Context.
- Output: `*-PATTERNS.md`.

S9: Planning
- Task(gsd-planner):
  - REQ: 1M enrichment if context window allows.
  - Sub-repos: Map to `sub_repos` field if applicable.
  - Interface Mapping: Planner extracts types to `<interfaces>` block.
  - REQ: `<read_first>` and `<acceptance_criteria>` (grep-verifiable) on EVERY task.
  - REQ: Concrete `<action>` values (no "align X with Y").

S10: Verification Loop (Plan Checker)
- Trigger: `plan_checker_enabled`.
- Task(gsd-plan-checker): Audit vs 10 Dimensions (Feasibility/Edge Cases/Nyquist/Naming/Specifics).
- Loop: Max 3 iterations. Revision -> Re-Plan.

S11: Handoff
- Show: Plan list, Wave breakdown, Estimated durations.
- Next: `/gsd-execute-phase {N}`.
</process>

<success_criteria>
- [ ] PRD Express path bypasses discussion.
- [ ] Safety gates (Security/UI/Schema) enforced.
- [ ] Planner injects `read_first` and `acceptance_criteria`.
- [ ] TDD heuristics applied if enabled.
- [ ] Patterns mapped before planning.
- [ ] 3-iteration revision loop functional.
</success_criteria>
