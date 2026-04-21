<purpose>
Ingest external docs (ADR, PRD, SPEC). Synthesize. Detect conflicts. Merge to .planning/.
</purpose>

<process>

S1: Setup
- Parse `--from <path>`. Default `.`.
- Ingest Mode: `new` (if no .planning/) | `merge`.
- Limit: 50 docs max.

S2: Discover
- Sources: Manifest file | Directory conventions (adr, prd, spec) | Heuristics.
- Logic: `AskUserQuestion` to approve discovered set.

S3: Ingest Engine
1. **Classify**: Spawn `gsd-doc-classifier` (parallel). Map doc -> type.
2. **Synthesize**: Spawn `gsd-doc-synthesizer`. Result -> `.planning/intel/`.
3. **Conflict Gate**: Engine `references/doc-conflict-engine.md`.
   - BLOCKER: Contradiction found -> Stop. No write.
   - WARNING: Overlap found -> `AskUserQuestion` to proceed.

S4: Route (New)
- Derive PROJECT.md fields.
- Delegate `gsd-roadmapper`. Produce: PROJECT, REQUIREMENTS, ROADMAP, STATE.

S5: Route (Merge)
- Merge new requirements/decisions/scope into existing artifacts.
- Preview diff -> `AskUserQuestion` to commit.

S6: Finalize
- Commit docs. Show ingest summary (decisions locked, requirements added).
</process>
