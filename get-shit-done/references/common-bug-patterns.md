# GSD Common Bug Patterns

Fast detection. Root cause signals.

## Patterns

| Signal | Probable Cause | Fix Protocol |
|--------|----------------|--------------|
| `Type error` | Signature drift. | Check imports + API. |
| `Infinite reload` | State loop (useEffect). | Audit dependencies. |
| `Module not found` | Pathing error. Case sensitivity. | Use Glob. Check `sdk`. |
| `Auth 401` | Token expiry. Missing header. | Check GSD secrets. |
| `Z-Index leak` | Context overlap. | Audit CSS layering. |

## Audit
1. `gsd-debugger` maps symptom to Pattern.
2. IF matches -> Run standard FIX.
3. IF novel -> Run `gsd-debugger-session`.
