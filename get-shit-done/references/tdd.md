# GSD TDD

Test Driven Development protocol.

## Objective
Ensure code correctness via executable evidence.

## Protocol
1. **Red**: Identify requirement. Write failing test (Unit/Mock).
2. **Green**: Implement minimal logic to pass.
3. **Refactor**: Clean up code style. Preserve pass state.

## Rules
- Every TASK in PLAN.md should cite a test file.
- If testing is impossible (e.g., untestable 3rd party UI), use **Observable Evidence** (screenshots/logs).
- Commit format: `fix([phase]): [id] pass tests`.
