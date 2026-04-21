# GSD Project Skills Discovery

Map project-specific tools and workflows.

## Objective
Detect `.gemini/` skills or project-specific scripts.

## Logic
1. Scan `.gemini/` for `.md` files.
2. Read `package.json` scripts.
3. Register tools in `MANIFEST.json`.
4. Enable agents to use "Custom Skills" during execution.
