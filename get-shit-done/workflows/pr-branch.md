<purpose>
Filter transient .planning/ artifacts from feature branch. Create clean PR-ready branch.
</purpose>

<process>

S1: Setup
- Target: `main` (default). Current: `$BRANCH`.
- Check: Ahead of target? On feature?

S2: Analysis
- Structural (Preserve): STATE, ROADMAP, MILESTONES, PROJECT, REQUIREMENTS, milestones/**.
- Transient (Drop): phases/**, quick/, research/, threads/, todos/, debug/, seeds/, codebase/, ui-reviews/.

S3: Rebuild
- Branch: `${CURRENT}-pr`.
- Loop: Cherry-pick commits `$TARGET..$CURRENT`.
- Filter: `git rm -r --cached .planning/{transient_dir}/` per commit.

S4: Verify
- Check diff: Commits count, Files count, .planning/ transient file count (should be 0).
- Suggest: `gh pr create --head ${PR_BRANCH}`.
</process>
