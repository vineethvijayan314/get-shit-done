<purpose>
Validate features via conversational testing. Create UAT.md to track progress. Feed gaps to planner.
</purpose>

<process>

S1: Initialize
- Parse Args: `${PHASE}`.
- `gsd-sdk query init.verify-work`.

S2: Session Management
- Check `find .planning/phases -name "*-UAT.md"`.
- If active sessions found: Show table (Phase | Status | Progress). Resume by number.
- If $ARGUMENTS: New session for phase.

S3: Automated UI Check (Optional)
- Trigger: Playwright/Puppeteer MCP available + `workflow.ui_phase`.
- Action: Open URL -> Screenshot -> Compare vs UI-SPEC.
- Status: Auto-pass matches. Queue manual review for subjective items.

S4: Test Extraction
- Read `*-SUMMARY.md`.
- Extract accomplishments -> observable user outcomes.
- Prepend "Cold Start Smoke Test" if infrastructure files modified.

S5: UAT File Construction
- Create `*-UAT.md`.
- Structure: Frontmatter (Status: testing) | Current Test | Tests (Pending) | Summary | Gaps.

S6: Presentation Loop
- `gsd-sdk query uat.render-checkpoint`.
- Display EXACTLY. No commentary.
- Wait for plain-text response (yes/y/ok -> Pass | skip -> Skip | issue msg -> Issue).

S7: Response Logic
- **Skip**: Reason inferred or provided.
- **Blocked**: Tags (server | physical-device | third-party). No gap entry.
- **Issue**:
  - Severity inferred: (crash/fails -> blocker | missing -> major | cosmetic -> cosmetic).
  - Entry: Append YAML Gap (truth, status: failed, reason, severity, test #).

S8: Batched Persistence
- Write to file: On issue / On checkpoint (every 5 passes) / On completion.

S9: Completion & Transition
- Status set: `complete` (all resovled) | `partial`.
- If issues == 0:
  - Check Security gate: `/gsd-secure-phase`.
  - Check UI gate: `/gsd-ui-review`.
  - **Inline Transition**: Follow `transition.md` logic (Mark phase complete in ROADMAP/STATE).
- If issues > 0: Proceed to Diagnosis.

S10: Diagnosis & Gap Planning
- **Diagnosis**: Invoke `diagnose-issues.md`. Parallel debug agents investigate.
- **Gap Plan**: Task(gsd-planner) --gaps mode.
- **Revision Loop**: Task(gsd-plan-checker) -> Issues? -> Re-Plan (Max 3).

S11: Ready Handoff
- Show: Gaps diagnosed | Fix plans created.
- Next: `/clear` -> `/gsd-execute-phase {phase} --gaps-only`.
</process>

<success_criteria>
- [ ] Active session resume functional.
- [ ] Cold start smoke test conditionally prepended.
- [ ] Checkpoint rendering byte-for-byte exact.
- [ ] Severity inferred without questions.
- [ ] Gaps structured for planner ingest.
- [ ] Auto-transition triggers on clear UAT.
</success_criteria>
