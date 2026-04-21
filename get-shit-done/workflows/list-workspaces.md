<purpose>
List active GSD workspaces based on config.
</purpose>

<process>

S1: Setup
- Read `config.json`. Identify `default_workspace_base`.

S2: Discovery
- `ls -d $default_workspace_base/*`.
- For each: Read `WORKSPACE.md` (if exists).

S3: Output
- Display Table: Name, Origin, Branch, Strategy.
</process>
