<purpose>
Idea capture. ZERO friction. Verbatim. Project or Global scope.
</purpose>

<process>

S1: Setup
- Strip flags: `--global`.
- Mode: `list` (if empty/list) | `promote <N>` | `append`.

S2: Append
- Dir: `.planning/notes/` (local) | `~/.claude/notes/` (global).
- Slug: First 4 words. Filename: `YYYY-MM-DD-slug.md`.
- Content: Frontmatter (date, promoted: false) + Verbatim text.
- Confirm one line: `Noted ({scope}): {text}`. No questions.

S3: List
- Show numbered list. Filter: `promoted: false`.
- Limit: Last 10 if >20 total.

S4: Promote
- Convert Note -> Todo.
- Create: `.planning/todos/pending/{NNN}-slug.md`.
- Update: `promoted: true` in source note.
</process>
