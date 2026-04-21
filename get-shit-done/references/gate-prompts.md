# GSD Gate Prompts

Standardized prompts for feedback gates.

## Objective
Enable clear `AskUserQuestion` calls. Force user decisions.

## Templates

### Concept Gate
"Goal: {goal}. Matches vision? Options: [Accept, Refine, Reject]"

### Context Gate
"Phase {N} context exists. Update? Options: [Update, Skip, View]"

### Plan Gate
"Ready to execute? Options: [Start, Edit Plan, Research Again]"

### Commit Gate
"Success verified. Commit changes? Options: [Commit, Revert, Dry Run]"
