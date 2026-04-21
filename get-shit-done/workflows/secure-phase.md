<purpose>
Verify threat mitigations. Reconcile PLAN.md threat register. Update SECURITY.md.
</purpose>

<process>

S0: Init
- `INIT=$(gsd-sdk query init.phase-op "${PHASE}")`.
- Resolve `gsd-security-auditor`.
- Check: `workflow.security_enforcement == true`.

S1: Detect State
- State A: Existing SECURITY.md -> Audit.
- State B: Existing PLAN + SUMMARY -> Run from source.
- State C: No SUMMARY -> Exit (Run `/gsd-execute-phase` first).

S2: Parse Threat Model
- Read PLAN.md -> Extract STRIDE register (ID, category, component, mitigation).
- Read SUMMARY.md -> Extract Threat Flags.

S3: Classification
- Status logic:
  - CLOSED: Mitigation found / Risk accepted in SECURITY.md.
  - OPEN: Unresolved.
- If `threats_open == 0` -> Skip to S6.

S4: User choice (TEXT_MODE)
- Options: 1. Verify all | 2. Accept all | 3. Cancel.

S5: Auditor Spawn
- Task(gsd-security-auditor).
- Prompt: Logic from `gsd-security-auditor.md`.
- Context: PLAN, SUMMARY, impl files, SECURITY.md.
- Rules: No code mods. Verify mitigations. Escalate gaps.

S6: Write SECURITY.md
- **New (State B)**: Use template `SECURITY.md`. Populate Audit Trail + Threat Register.
- **Update (State A)**: Update statuses. Append audit log (Found/Closed/Open).

S7: Guard Gate
- If `threats_open > 0`: BLOCK phase advancement. No next steps.

S8: Wrap
- `git commit`: `docs(phase-${PHASE}): security mitigation verification`.
- On Success: `/gsd-validate-phase {N}` | `/gsd-verify-work {N}`.
</process>

<success_criteria>
- [ ] Enforcement bypass checked.
- [ ] STRIDE register parsed accurately.
- [ ] threats_open > 0 BLOCKS advancement.
- [ ] SECURITY.md updated with evidence.
</success_criteria>
