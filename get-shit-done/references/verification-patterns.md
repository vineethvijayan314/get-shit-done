# GSD Verification Patterns

Reusable test strategies.

## Patterns

| Logic Type | Strategy | Tool |
|------------|----------|------|
| **Pure Logic** | Unit Test. | Jest / Vitest. |
| **API/Route** | Integration Test. | Supertest / Curl. |
| **UI/UX** | Screenshot + Linter. | browser_subagent. |
| **State** | Snapshot check. | JSON diff. |
| **Infra** | Dependency map check. | Glob / ls. |

## Verification order
1. Internal (Unit).
2. Integration (E2E/API).
3. Final Audit (manual/visual).
