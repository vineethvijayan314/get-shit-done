<purpose>
Self-update GSD. Fetch changelog. Backup custom files. Clean install.
</purpose>

<process>

S1: Detect
- Resolve `INSTALLED_VERSION` (0.0.0 if unknown).
- Scope: `LOCAL` | `GLOBAL`. Runtime: `claude|opencode|gemini|codex`.

S2: Fetch
- Check `npm view get-shit-done-cc version`.
- IF version ahead/equal -> Exit.
- IF upgrade available -> Fetch GitHub CHANGELOG.md -> `AskUserQuestion` (show delta).

S3: Backup
- Dir: `gsd-user-files-backup/`.
- Logic: `gsd-tools detect-custom-files`. Copy any file not in `gsd-file-manifest.json` from GSD managed dirs.

S4: Install
- Cmd: `npx -y get-shit-done-cc@latest --{runtime} --{scope}`.
- Clear Cache: `rm -f cache/gsd-update-check.json` (all runtimes).

S5: Post
- Reminder: Restart runtime.
- Patch Check: If `gsd-local-patches/` exists -> suggest `/gsd-reapply-patches`.
</process>
