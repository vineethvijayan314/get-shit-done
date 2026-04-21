# GSD Planning Config
Schema for `.planning/config.json`.

## Core Fields
- `project_code`: 3-4 char slug.
- `model_profile`: budget | balanced | quality | inherit.
- `branching_strategy`: none | phase | milestone.
- `commit_docs`: true | false.
- `yolo`: true (autonomous) | false (interactive).

## Workflow Flags
- `research`: Enable discovery agents.
- `plan_check`: Enable adversarial audit.
- `verifier`: Enable goal-backward validation.
- `nyquist_validation`: Force test evidence.
- `auto_advance`: Chain phases.
