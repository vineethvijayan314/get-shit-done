<purpose>
Verify phase goals. Goal-backward analysis. Truths -> Artifacts -> Wiring -> Tests.
</purpose>

<process>

S1: Setup
- `INIT=$(gsd-sdk query init.phase-op "${PHASE}")`.
- Load: `ROADMAP.md` (goal), `REQUIREMENTS.md` (traceability), `SUMMARY.md`.

S2: Must-Haves
- Source A: PLAN frontmatter `must_haves` (truths, artifacts, links).
- Source B: ROADMAP `success_criteria` array.
- Fallback: Derive behaviors from phase goal.

S3: Truth Verification
- Status: ✓ VERIFIED | ✗ FAILED | ? UNCERTAIN.
- Logic: Truth T enabled? -> Artifacts A exist/substantive? -> Wiring W connected?

S4: Artifact Audit
- `ARTIFACT_RESULT=$(gsd-sdk query verify.artifacts "$plan")`.
- Checks: exists (L1), substantive (L2), wired/imported (L3).
- Spot check: Unused exports found? (WARNING).

S5: Wiring Audit
- `LINKS_RESULT=$(gsd-sdk query verify.key-links "$plan")`.
- Patterns: Comp->API, API->DB, Form->Handler, State->Render.

S6: Behavioral Verification
- Action: Run test suite (timeout 5m).
- Detect: npm | cargo | go | pytest.
- Checks: Run CLI success criteria commands with fixtures.
- Gate: Behavioral failure = BLOCKER.

S7: Test Quality Audit
- Scans: Disabled tests (`.skip`), circular fixtures (engine-generated), assertion strength (existence vs value), provenance (external source oracle).
- Rule: proving requirement with skipped/circular test = BLOCKER.

S8: Human Items
- Viz, user flow, real-time sync, performance feel.

S9: Decision Tree
- IF gap/stub/failed/circular -> `gaps_found`.
- IF human items exist -> `human_needed`.
- ELSE -> `passed`.

S10: Deferral
- Filter gaps against later phases in ROADMAP.
- If gap explicitly covered later -> `deferred`.

S11: Report
- Write `{N}-VERIFICATION.md`.
- Include: Gap summary + autonomous fix plans.
</process>

<success_criteria>
- [ ] Goal-backward truths verified.
- [ ] Behavioral tests run + reported.
- [ ] Test quality audit complete.
- [ ] Fix plans generated for gaps.
</success_criteria>
