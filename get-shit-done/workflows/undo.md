<purpose>
Roll back GSD commits. Safe revert. Preserve history. No resets.
</purpose>

<process>

S1: Setup
- Parse: `--last N` | `--phase NN` | `--plan NN-MM`.
- Guard: Dirty tree? (abort if modified files outside .planning/).

S2: Gather
- Source A (Phase): `.phase-manifest.json` -> `commits` array. Fallback: git log search.
- Source B (Plan): git log filter `(NN-MM)`.
- Source C (Last): git log -N. `AskUserQuestion` to select.

S3: Deps
- Check: Do later phases depend on target?
- Check: Do later plans in phase consume target outputs?
- Alert -> `AskUserQuestion` to proceed anyway.

S4: Execute
- Reverse order (newest first).
- Command: `git revert --no-commit ${HASH}`.
- Conflict -> Abort + `git reset HEAD` + `git restore .` (cleanup).
- Success -> Single commit: `revert({target}): {reason}`.

S5: Wrap
- /gsd-progress next.
</process>
