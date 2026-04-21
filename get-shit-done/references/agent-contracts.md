# GSD Agent Contracts

Handoff protocol. IO schema. State guarantees.

## Agent Types
- **Producer**: Writes new artifacts (Planner, Writer).
- **Auditor**: Reviews artifacts (Checker, Reviewer).
- **Executor**: Modifies source (Code Fixer, Debugger).

## Contract Rules
- Input: `args` JSON.
- Output: Structured markdown or JSON.
- Context: Must read mandatory references cited in definition.
- Integrity: Do not overwrite user-manual annotations.
- Errors: Return CLEAR blockers. No fluff.
