<purpose>
Create isolated workspace with worktrees/clones and local .planning/ dir.
</purpose>

<process>

S1: Setup
- `INIT=$(gsd-sdk query init.new-workspace)`.
- Parse `$ARGUMENTS`: `--name` (REQ), `--repos`, `--path`, `--strategy` (worktree|clone), `--branch`.

S2: Repo Selection
- If `--repos` missing:
  - If child repos found -> Select from list.
  - If current repo git -> Use current.
  - Else -> Error.

S3: Strategy Choice
- Default: `worktree`. Fallback: `clone`.

S4: Validation
- Target path empty?
- Source repos valid git?
- Worktree available?

S5: Creation Loop
- `mkdir -p "$TARGET_PATH"`.
- Per repo:
  - Worktree: `git worktree add "$TARGET_PATH/$NAME" -b "$BRANCH"`.
  - Clone: `git clone "$SOURCE" "$TARGET"`.
- Write `WORKSPACE.md` manifest.
- Init `$TARGET/.planning/`.

S6: Wrap
- Output: Success count + branch.
- Choice: Init GSD project now? -> `/gsd-new-project`.
</process>

<success_criteria>
- [ ] Member repos copied via strategy.
- [ ] WORKSPACE.md manifest written.
- [ ] .planning/ dir initialized.
</success_criteria>
