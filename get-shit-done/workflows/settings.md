# Workflow: Settings
Trigger: `/gsd-settings`

## S1: Setup
- Logic: `gsd-sdk query config-path`.
- Load: Current `config.json`.

## S2: Edit
- Interactive/Text mode.
- Categories: research, plan_check, verifier, auto_advance, model_profile, use_worktrees.

## S3: Save
- Action: Update `config.json`.
- Confirm: Show settings table.
