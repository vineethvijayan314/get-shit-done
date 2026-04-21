<purpose>
Delete workspace directory. Cleanup git worktrees if applicable.
</purpose>

<process>

S1: Setup
- Parse `$ARGUMENTS`: `NAME`.
- Resolve path via `config.json`.

S2: Cleanup Logic
- Check `WORKSPACE.md` for strategy.
- If `worktree`:
  - Per member repo: `git worktree remove "$PATH"`.
- Else:
  - `rm -rf "$WORKSPACE_PATH"`.

S3: Sync
- Verify path gone.
</process>

<success_criteria>
- [ ] Worktree reference removed from source git repo.
- [ ] Disk space reclaimed.
</success_criteria>
