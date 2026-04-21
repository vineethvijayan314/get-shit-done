# GSD Planning Config

System configuration for GSD planning engine.

## Model Mapping
| Tool | Target Model | Profile |
|------|--------------|---------|
| `gsd-planner` | sonnet-3.5 | reasoning |
| `gsd-executor` | sonnet-3.5 | velocity |
| `gsd-debugger` | o1 / reasoning | deep-think |

## Standard Paths
- `ROOT/.planning/ROADMAP.md`
- `ROOT/.planning/STATE.md`
- `ROOT/.planning/CONTEXT.md`
- `ROOT/.planning/tasks/{phase}.md`

## Protocols
- **COMMIT**: "TASK_COMMIT_CONVENTION".
- **VERIFY**: "DUAL_LAYER_VERIFICATION".
- **CAVEMAN**: "FULL" (article-free).
