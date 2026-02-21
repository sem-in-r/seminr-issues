---
name: repo-setup
description: Set up CLAUDE.local.md for a new contributor to the seminr-issues repo. Use when a maintainer needs to configure their local environment.
disable-model-invocation: true
allowed-tools: Read, Glob, Bash(ls *), Bash(test *), Bash(realpath *), Bash(dirname *)
---

# Repo Setup

Set up `CLAUDE.local.md` so this repo can access the local seminr codebase.

## Steps

1. **Check if already configured**: Read `CLAUDE.local.md` in the project root. If it exists and has content, show it to the user and ask if they want to reconfigure or keep it.

2. **Locate the seminr repo**: Check if a sibling `seminr` directory exists at `../seminr` relative to this repo's root. Verify it's a git repo with `test -d ../seminr/.git`.

   - **If found**: Tell the user you detected the seminr repo at that absolute path and ask them to confirm.
   - **If not found**: Ask the user where their local clone of `sem-in-r/seminr` is. Recommend cloning it as a sibling directory:
     ```
     cd <parent of seminr-issues>
     git clone git@github.com:sem-in-r/seminr.git
     ```

3. **Worktrees directory**: Check if `../seminr-worktrees/` exists as a sibling.

   - **If found**: Note it and confirm with the user.
   - **If not found**: Ask the user if they want to set up a worktrees directory. Recommend creating it as a sibling:
     ```
     mkdir ../seminr-worktrees
     ```

4. **Write `CLAUDE.local.md`**: Once paths are confirmed, write the file using this template (substitute actual absolute paths):

```markdown
# CLAUDE local environment

## SEMinR Codebase

Local seminr source (for code investigation, git history, running tests):
`<SEMINR_PATH>`

Worktrees: `<WORKTREES_PATH>`

## Planning Documents

Main development queue: @issues-triage.md

Other documents (read on demand, not auto-loaded):
- `develop-upcoming.md` — PRs merged to develop, issues to close on next release
- `releases/released-2.4.2.md` — release history, closed issues, archived PRs
```

If the user opted out of worktrees, omit the `Worktrees:` line.

5. **Verify**: Confirm the file was written and show the user a summary of what was configured.
