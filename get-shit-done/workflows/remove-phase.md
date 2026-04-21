<purpose>
Delete phase. Re-index trailing phases. Orphan requirements.
</purpose>

<process>

S1: Init
- `ROADMAP=$(cat .planning/ROADMAP.md)`.
- Parse `$ARGUMENTS`: `INDEX`.

S2: Deletion Logic
- Confirm phase exists.
- Guard: Is phase already complete? -> Warn.
- Unmap requirements: Move mapped REQ-IDs to "Unmapped" in ROADMAP.md.
- Delete directory: `.planning/phases/XX-{NAME}`.

S3: Re-indexing Logic
- Shift trailing phases: `N -> N-1`.
- Update directory names in `.planning/phases/`.
- Update requirement traceability maps.

S4: ROADMAP Sync
- Update `ROADMAP.md` table + phase details.
- Update `STATE.md` current position if deletion affects it.

S5: Wrap
- `git commit`: `roadmap: remove Phase {INDEX}`.
- Next: `/gsd-progress`.
</process>

<success_criteria>
- [ ] Phase removed + index shifted.
- [ ] Requirement orphans tracked.
- [ ] Directory structure synced with roadmap.
</success_criteria>
