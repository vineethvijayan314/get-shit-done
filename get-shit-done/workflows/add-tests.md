<purpose>
Generate unit/E2E tests for completed phase. Classify files (TDD/E2E/Skip). Approve plan. Generate RED-GREEN tests.
</purpose>

<process>

S1: Parse Args
- `$PHASE_ARG`: Phase number.
- `$EXTRA_INSTRUCTIONS`: Optional text.
- REQ: `/gsd-add-tests <phase>`.

S2: Load Context
- `gsd-sdk query init.phase-op "${PHASE_ARG}"`.
- REQ: `${phase_dir}/*-SUMMARY.md`.
- Banner: `ADD TESTS — Phase ${phase_number}`.

S3: Analyze Implementation
Classify modified files (from SUMMARY.md):
- **TDD (Unit)**: Pure functions. Math, logic, transforms, validators.
- **E2E (Browser)**: UI behavior. Nav, forms, shortcuts, modals, drag-drop.
- **Skip**: CSS, config, glue, migrations, stubs, types.
- Rule: Read file content for classification. NO filename-only guessing.

S4: Present Classification
- Use `AskUserQuestion`. Show TDD/E2E/Skip counts + reasons.
- Modes: Approve | Adjust | Cancel.

S5: Discover Test Structure
- `find` test dirs (`__tests__`, `spec`).
- ID conventions (`.test.ts`, `.spec.ts`).
- ID runners (`package.json`, `.sln`).

S6: Generate Test Plan
- TDD Plan: RED-GREEN-REFACTOR. List inputs/outputs/edge cases.
- E2E Plan: User scenarios from CONTEXT/VERIFICATION. Describe Action -> Outcome -> Assertion.
- Present Plan: `Generate all` | `Cherry-pick` | `Adjust`.

S7: Execute TDD Generation
- Create file. conventions (naming/imports) REQ.
- Write test: Arrange -> Act -> Assert.
- Run. Result:
  - Pass: OK.
  - Fail (Logic): Flag as BUG. NO patching.
  - Fail (Error): Fix test code.

S8: Execute E2E Generation
- Check collisions (`grep`). Extend existing or create new.
- Run. Result:
  - GREEN: Succcess.
  - RED: Flag as BUG.
  - Blocker: Report. NEVER mark success without execution.

S9: Summary & Commit
- Category Table: Generated | Passing | Failing | Blocked.
- `gsd-sdk query state-snapshot`.
- Commit (if passing): `test(phase-${phase_number}): add unit and E2E tests`.
- Next steps (fixes/verify).
</process>

<success_criteria>
- [ ] SUMMARY.md + CONTEXT.md loaded.
- [ ] Files classified TDD/E2E/Skip.
- [ ] Test plan approved by user.
- [ ] TDD results verified (RED/GREEN).
- [ ] E2E scenarios ran. NO fake passes.
- [ ] Bugs flagged.
- [ ] Test files committed.
</success_criteria>
