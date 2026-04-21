<purpose>
Insert phase at specific index. Re-index trailing phases. Shift SUCCESS_CRITERIA references.
</purpose>

<process>

S1: Init
- `ROADMAP=$(cat .planning/ROADMAP.md)`.
- Parse `$ARGUMENTS`: `INDEX`, `NAME`, `GOAL`.

S2: Re-indexing Logic
- Identify target index.
- Shift all phases >= index: `N -> N+1`.
- Update directory names in `.planning/phases/`.
- Update requirement traceability maps in `REQUIREMENTS.md`.

S3: Insertion
- Add new phase block to ROADMAP.md.
- Create new phase directory with README.md goal.

S4: Integrity Check
- Verify no duplicate phase numbers.
- Verify requirement mapping continuity.

S5: Wrap
- `git commit`: `roadmap: insert Phase {INDEX} - {NAME}`.
- Next: `/gsd-discuss-phase {INDEX}`.
</process>

<success_criteria>
- [ ] Phases shifted without data loss.
- [ ] Directory names match roadmap indices.
- [ ] Traceability map updated.
</success_criteria>
