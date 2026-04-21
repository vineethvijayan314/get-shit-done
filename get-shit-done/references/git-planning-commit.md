# GSD Git Planning Commit

Commit protocol for planning artifacts.

## Protocol
1. New phase roadmap update.
2. CONTEXT.md lock.
3. PLAN.md creation.

## Format
- Roadmap: `docs(roadmap): add phase {N} {name}`
- Context: `docs(context): {N} decisions locked`
- Plan: `docs(plan): {N} tasks defined`

## Rule
- Stage `.planning/` files ONLY. No source code.
