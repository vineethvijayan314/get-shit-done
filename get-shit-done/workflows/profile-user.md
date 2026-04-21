<purpose>
Developer profiling. Experience audit. Style alignment. Consent-first.
</purpose>

<process>

S1: Consent
- `AskUserQuestion(question: "GSD needs to profile your work patterns. Proceed?", options: [Yes, No])`.
- IF YES -> Check for `~/.gsd/profiles/global.json`.

S2: Data Scan
- Source 1: Recent git sessions (author patterns, comment styles).
- Source 2: `.planning/learnings/` (past project choices).
- Source 3: Codebase archetypes.

S3: Refine
- IF data weak -> `AskUserQuestion` (Questionnaire Mode).
- Fields: Tech Stack, PR Style, Communication Tone, Bias for Action vs Research.

S4: Generate
- Agent: `gsd-user-profiler`.
- Artifact: `.planning/DEVELOPER-PROFILE.md`.
- Profile Tags: {Primitive, Token-Efficient, Technical, terse}.

S5: Sync
- Offer to save to `~/.gsd/profiles/global.json` for all projects.
</process>
