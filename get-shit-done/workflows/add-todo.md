<purpose>
Capture idea/task/issue as structured todo. Enable "thought -> capture -> continue" flow.
</purpose>

<process>

S1: Load Context
- `gsd-sdk query init.todos`.
- `mkdir -p .planning/todos/{pending,completed}`.

S2: Extract Content
- With Args: Title = all args.
- NO Args: Analyze recent chat.
- formulated: `title` (3-10 words, action verb), `problem` (why), `solution` (hints | TBD), `files` (paths + lines).

S3: Infer Area
Map paths to labels:
- `api/*` -> `api`.
- `ui/*` -> `ui`.
- `auth/*` -> `auth`.
- `database/*` -> `database`.
- `tests/*` -> `testing`.
- `docs/*` -> `docs`.
- `scripts/*` -> `tooling`.
- Unclear -> `general`.

S4: Check Duplicates
`grep -l -i "[key words]" .planning/todos/pending/*.md`.
If match: `AskUserQuestion`. Skip | Replace | Add anyway.

S5: Create File
- `slug=$(gsd-sdk query generate-slug "$title" --raw)`.
- Path: `.planning/todos/pending/${date}-${slug}.md`.
- Content: Frontmatter (created, title, area, files) + ## Problem + ## Solution.

S6: Update State
If STATE.md exists: Update `### Pending Todos` count under `Accumulated Context`.

S7: Commit
`gsd-sdk query commit "docs: capture todo - [title]"`.
Confirm "Committed...".
</process>

<success_criteria>
- [ ] Todo file created with frontmatter.
- [ ] Problem context sufficient for future retrieval.
- [ ] No duplicates.
- [ ] STATE.md synced.
- [ ] Git commit successful.
</success_criteria>
