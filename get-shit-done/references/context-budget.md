# GSD Context Budget

Token management. Context window optimization.

## Strategy: Sharding
- Read 5-15 files max per turn.
- Use `intel/` artifacts instead of raw code where possible.
- Truncate SESSION-LOG.md after 10 turns.

## Strategy: Caveman
- Use "Full" or "Ultra" mode for all prompts.
- Strip articles and fluff.
- Estimated saving: 40-70% tokens.

## Guard
- IF budget > 80% (Model Limit) -> Trigger `gsd-cleanup`.
- Archive old plans. Compress logs.
