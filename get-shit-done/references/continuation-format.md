# GSD Continuation Format

Resume context. Session bridging.

## Objective
Enable new agent session to inherit precise state from previous session.

## Format
File: `.planning/CONTINUATIONS.md`.

| Key | Value |
|-----|-------|
| `Last Phase` | [ID] |
| `Last Commits` | [hashes] |
| `Blocks` | [desc] |
| `Intent` | [phase goal] |
| `Instruction` | "Execute /gsd-execute-phase" |

## Logic
1. `gsd-resume-project` reads latest continuation.
2. Synces CLI arguments.
3. Pre-loads relevant files to context.
