<purpose>
Analyze codebase. Produce 7 docs in .planning/codebase/. Parallel or Sequential.
</purpose>

<process>

S1: Setup
- Load context: `gsd-sdk query init.map-codebase`.
- Check existing: skip | update | refresh.
- Create dir: `.planning/codebase/`.

S2: Strategy
- IF `Task` tool available -> Spawn 4 parallel `gsd-codebase-mapper` agents.
- ELSE -> Run 4 sequential passes inline using FS tools.

S3: Passes (Focus Areas)
- Tech: STACK.md (runtime/deps), INTEGRATIONS.md (APIs/DB).
- Arch: ARCHITECTURE.md (entry/dataflow), STRUCTURE.md (layout).
- Quality: CONVENTIONS.md (style), TESTING.md (mocking/framework).
- Concerns: CONCERNS.md (debt/security).

S4: Secret Scan
- `grep -E <SECRET_PATTERNS> .planning/codebase/*.md`.
- Alert user if keys leaked.

S5: Wrap
- Commit: `docs: map existing codebase`.
- Show line counts + /gsd-new-project next step.
</process>
