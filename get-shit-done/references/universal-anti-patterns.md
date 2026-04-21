# GSD Universal Anti-Patterns

Critical failure modes to avoid system-wide.

## Traps
- **Context Overload**: Feeding 100 files to LLM. (Use `sharding`).
- **Logic Hallucination**: Assuming API exists without `grep`. (Use `scouting`).
- **Instruction Drift**: Ignoring hard constraints in `CLAUDE.md`. (Scan mandatory files).
- **Silent Failure**: Logic fails but process continues. (Require `tests/evidence`).
- **Git Bloat**: Committing `node_modules` or `tmp`. (Sync `.gitignore`).

## Audit
- All Auditors/Reviewers must check for these flags.
- IF High Risk present -> Total Stop.
