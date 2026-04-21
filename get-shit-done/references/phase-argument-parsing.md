# GSD Phase Argument Parsing

CLI argument handling.

## Standards
- `--phase [N]`: Specific phase ID.
- `--decimal [N.M]`: Sub-phase ID.
- `--force`: Bypass setup gates (CAUTION).
- `--context [path]`: Override project context.

## Logic
1. Validate format via `gsd-eval-auditor`.
2. Map input to `.gsd/manifest.json`.
3. IF invalid -> Return logic error. Stop.
