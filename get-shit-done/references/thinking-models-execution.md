# GSD Thinking Model: Execution

Cognitive framework for `gsd-executor`.

## Framework
1. **Intake**: Map Task instructions to file content.
2. **Draft**: Generate minimal diff.
3. **Verify**: Run lint. Run project tests.
4. **Commit**: Apply task commit naming convention.

## Rules
- Atomic changes.
- NO deviation without permission (Ask User).
- Track state hash per step.
