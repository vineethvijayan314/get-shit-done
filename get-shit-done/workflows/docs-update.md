<purpose>
Canonical doc update. Parallel wave-based generation. Manifest tracking. Integrity verify. Fix loop.
</purpose>

<process>

S1: Setup
- Resolve `OUTPUT_DIR`. Scan `.planning/intel/` + `docs/`.
- Heuristics: Detect project doc structure (Type 1: Root, Type 2: docs/, Type 3: Hybrid).
- Options: `--full` (all) | `--focus <area>` | `--gaps` (missing only).

S2: Discover
- Entrypoint: `gsd-doc-orchestrator`.
- Build `DOC-MANIFEST.json`: path, type, source_files, status (pending/wave1/verify/done).

S3: Wave 1 (Base Layer)
- Goal: System overview, PRD, ARCHITECTURE.
- Dispatch: `gsd-doc-writer` (parallel).
- Verification: `gsd-doc-verifier`. Check against codebase logic.

S4: Wave 2 (Detail Layer)
- Goal: Components, API, Guides.
- Logic: Consume Wave 1 outputs for consistency.

S5: Integrity Loop
1. **Analyze**: Check verifier flags.
2. **Fix**: Dispatch `gsd-doc-fixer`.
3. **Limit**: Stop loop after 3 unsuccessful attempts -> notify user.

S6: Finalize
- Metadata: Update `VERSION` / `LAST_REVIEWED`.
- Commit manifest + updated docs.
</process>
