<purpose>
Audit Nyquist validation gaps. Generate missing tests. Update VALIDATION.md.
</purpose>

<process>

S0: Init
- `INIT=$(gsd-sdk query init.phase-op "${PHASE}")`.
- Resolve `gsd-nyquist-auditor`.
- Gate: `workflow.nyquist_validation == true`.

S1: Detect State
- State A: Existing VALIDATION.md -> Audit.
- State B: PLAN + SUMMARY exists -> Reconstruct mapping.
- State C: No SUMMARY -> Exit (Run `/gsd-execute-phase`).

S2: Discovery
- Map REQ-IDs to task lists from artifacts.
- Infrastructure check: find `pytest.ini`, `jest.config.*`, `pyproject.toml`.
- Cross-ref: requirement -> test file -> status (green/fail/none).

S3: Gap Analysis
- Classify REQs:
  - COVERED: Green test exists.
  - PARTIAL: Broken/Incomplete test.
  - MISSING: No test match.
- If Gaps found -> Present Table + Options (Fix | Manual-Only | Cancel).

S4: Auditor Spawn
- Task(gsd-nyquist-auditor).
- Prompt: Logic from `gsd-nyquist-auditor.md`.
- Rules: No implementation mods. Max 3 debug iterations. Escalate bugs.

S5: Write VALIDATION.md
- **New (State B)**: Use template. Map REQs.
- **Update (State A)**: Appent audit trail. Update status.

S6: Wrap
- `git commit`: `test(phase-${PHASE}): Nyquist validation tests`.
- Next: `/gsd-audit-milestone`.
</process>

<success_criteria>
- [ ] REQ-to-test mapping verified.
- [ ] Gap analysis accurately identifies coverage holes.
- [ ] Auditor resolves gaps without implementation side-effects.
- [ ] VALIDATION.md updated with evidence.
</success_criteria>
