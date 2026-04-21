<purpose>
Interactive config: GSD agents (research, plan_check, verifier) + model profile.
</purpose>

<process>

S1: Setup
- Resolve config path: `gsd-sdk query config-path`.
- Load current: `GS_CONFIG=$(cat $PATH)`.

S2: Values
- `workflow.research`: Spawn researcher?
- `workflow.plan_check`: Spawn plan checker?
- `workflow.verifier`: Spawn execution verifier?
- `workflow.auto_advance`: Chain stages?
- `model_profile`: quality | balanced | budget | inherit.
- `git.branching_strategy`: none | phase | milestone.
- `workflow.use_worktrees`: agent isolation via worktrees?

S3: Interaction
- `AskUserQuestion(options[])`.
- Mode: Text (if `--text` flag or `text_mode: true`).

S4: Save
- Merge into `config.json`.
- Optional: Save as global defaults (~/.gsd/defaults.json).

S5: Confirm
- Output settings table.
</process>
