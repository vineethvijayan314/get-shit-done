<purpose>
Add phase to end of milestone. Append to ROADMAP.
</purpose>

<process>

S1: Setup
- Read ROADMAP.md. Parse `$ARGUMENTS`: `NAME`, `GOAL`.

S2: Logic
- Identify next index `N+1`.
- Append phase block to ROADMAP.md.
- Create directory `.planning/phases/XX-{NAME}`.
- Update `STATE.md` phase count.

S3: Wrap
- `git commit`: `roadmap: add Phase {N+1} - {NAME}`.
</process>

<success_criteria>
- [ ] Roadmap table + block appended.
- [ ] Directory structure initialized.
</success_criteria>
