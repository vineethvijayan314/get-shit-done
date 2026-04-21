<purpose>
Extract implementation decisions for downstream agents (researcher, planner). Think-partner flow to identify gray areas, deep-dive choices, and capture vision.
</purpose>

<process>

S1: Initialize
- Parse Args: `${PHASE}`, `--power`, `--all`, `--auto`, `--chain`, `--text`.
- `gsd-sdk query init.phase-op`.
- Translate output if `response_language` set.

S2: Guards & Blocking
- Check `${phase_dir}/.continue-here.md`.
- REQ: If `severity="blocking"`, answer 3 questions: What? Manifest? Structural fix?
- Check `SPEC.md`. If found -> Lock requirements. Focus ONLY on implementation (HOW).

S3: Check Existing & Checkpoint
- If CONTEXT.md exists: `AskUserQuestion`. Update | View | Skip.
- If `*-DISCUSS-CHECKPOINT.json` exists: `AskUserQuestion`. Resume | Start fresh.
- If plans exist: Warn user. Decisions won't affect existing plans without replan.

S4: Prior Context & Code Scout
- Read PROJECT.md, REQUIREMENTS.md, STATE.md.
- Read prior CONTEXT.md for locked preferences.
- Load spike/sketch findings.
- `scout_codebase`: Targeted `grep` for phase terms. Identify reusable assets & integration points.

S5: Identify Gray Areas
- Logic: Domain analysis (See/Call/Run/Read/Organize).
- REQ: specific, not generic.
- Check flags:
  - `NON_TECHNICAL_OWNER`: Reframe to product/outcome language.
  - `ADVISOR_MODE`: resolve `vendor_philosophy` calibration.
- REQ: No scope creep. Move to "Deferred Ideas" section if user adds features.

S6: Selection & Research (Advisor)
- If `--auto/--all`: select all gray areas.
- If `ADVISOR_MODE`:
  - Spawn `gsd-advisor` (parallel Tasks).
  - Resolve research tables: [Option | Pros | Cons | Complexity | Recommendation].
  - Synthesis: Weave project context. Trim options by calibration.

S7: Discussion Loop
Interactive loop per selected area.
- If `ADVISOR_MODE`: Table-first flow. Pick from research options.
- If `discuss_only`: standard Q&A.
- Flags:
  - `--analyze`: provide trade-off table before question.
  - `thinking_partner`: analyze competing priorities if detected.
- **Answer Validation**: REQ non-empty response. Retry once then fallback to plain-text list.

S8: Checkpoint & Finalize
- Save partial progress to `*-DISCUSS-CHECKPOINT.json` after each area.
- Final: `gsd-sdk query context.write`.
- Committed: `docs(${padded_phase}): create/update phase context`.

S9: Completion
- Show: Decisions locked, Items deferred, Open questions.
- Handoff: `/gsd-plan-phase` (or auto if `--chain`).
</process>

<success_criteria>
- [ ] Gray areas derived from domain + code context (not generic).
- [ ] Prior decisions respected (no re-asking).
- [ ] SPEC.md respected (no requirement negotiation).
- [ ] Checkpoint logic enables resume.
- [ ] Advisor mode provides comparison tables.
- [ ] Non-technical owner reframing active (if applicable).
- [ ] CONTEXT.md structure matches template.
</success_criteria>
