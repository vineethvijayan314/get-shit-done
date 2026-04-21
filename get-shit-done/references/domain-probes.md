# GSD Domain Probes

Extract logic from complex domains.

## Objective
Enable `gsd-domain-researcher` to ask high-value questions about unknown tech stacks or business logic.

## Probe Categories

| Category | Goal |
|----------|------|
| **Data Lifecycle** | How is [Entity] created? How does it die? |
| **Auth Chain** | Who authorizes [Action]? Where is the token held? |
| **Edge Cases** | What happens if [Dependency] fails? |
| **Integration** | Who consumes [API]? |

## Process
1. Run `gsd-ai-researcher` for base docs.
2. Formulate 3-5 specific Probes.
3. Subagent `gsd-domain-researcher` answers Probes via codebase scan.
