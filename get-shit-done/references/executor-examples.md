# GSD Executor Examples

Reference patterns for `gsd-executor`.

## Pattern: Logic Refactor
Goal: Move logic from A to B.
1. Draft move.
2. Update imports.
3. Fix lint.
4. Verify tests pass.
5. Commit fix: `fix([phase]): [id] move logic`.

## Pattern: Feature Add
Goal: Add new endpoint.
1. Create file.
2. Define schema.
3. Implement handler.
4. Add integration test.
5. Commit feat: `feat([phase]): [id] new endpoint`.

## Rule
- Small commits. 1-10 files. All verified.
