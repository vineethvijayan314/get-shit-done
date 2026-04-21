# GSD Planner Antipatterns

Avoid these traps.

## High Risk
- **Mega-Phases**: > 50 files in one task. (Split them).
- **Ambiguity**: "Refactor system" as objective. (Be specific).
- **Tool-Less plans**: "Think about X" as task. (Task must be actionable).
- **Circular dependencies**: Phase A requires B, B requires A. (Linearize).

## Audit
- `gsd-plan-checker` flags these during audit.
- IF 1+ High Risk found -> Reject plan.
