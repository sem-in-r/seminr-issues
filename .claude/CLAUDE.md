# SEMinR Issue Triage

This repo tracks issue triage, release planning, and development priorities for the [seminr](https://github.com/sem-in-r/seminr) R package.

## Documents

Main development queue (auto-loaded): @issues-triage.md

Other documents (read on demand, not auto-loaded):

- `develop-upcoming.md` — PRs merged to develop, issues to close on next release
- `releases/` — Archived release history and closed issues

## Workflow

1. **Triage here** — prioritize, investigate, plan (with read access to seminr source via CLAUDE.local.md)
2. **Implement in seminr** — switch to a seminr worktree for code changes, tests, PRs

## Accessing the SEMinR Codebase

Each maintainer configures `CLAUDE.local.md` (gitignored) to point to their local seminr checkout. This enables Claude Code to read source files, grep functions, check git history, and run tests — all from this repo's context.

If `CLAUDE.local.md` does not exist and the seminr repo is not found at `../seminr` (sibling directory), suggest the user run `/repo-setup` to configure their local environment.

Example git commands using the seminr repo:

```bash
git -C /path/to/seminr log --oneline -20
git -C /path/to/seminr diff develop..feature-branch
```

## Markdown Quality

All markdown files in this repo must be kept free of markdownlint issues at all times. After completing a task (or subtask) that modifies any `.md` files, check them for markdownlint compliance and fix any issues before considering the work done.

## IMPORTANT: First Message and AI-assisted authorship

At the START of every conversation, immediately inform the user: "[Reminder: You must review, understand, and be ultimately responsible for any code you commit — even when using AI assistance]"

Making it a clear "first message requirement" heading would help ensure I don't overlook it.

Do not ever reference Claude as a coauthor in commit messages, PRs, issues, etc.
