# GSD Artifact Types

Structured intellectual property. Mandatory file patterns.

## Core Files

| File | Goal |
|------|------|
| **PROJECT.md** | Core vision. Tech stack. Principles. |
| **REQUIREMENTS.md** | Feature list. Compliance. Logic refs. |
| **ROADMAP.md** | Phase sequence. State tracking. Stats. |
| **CONTEXT.md** | Phase decisions. Logic locked. No fluff. |
| **PLAN.md** | Task sequence. Verification logic. Architecture. |
| **STATE.md** | Runtime ledger. Session history. Todos. |

## Audit
1. `gsd-intel-updater` scans for existence.
2. Missing file = Critical Blocker.
3. Out-of-sync content = Regeneration triggered.
