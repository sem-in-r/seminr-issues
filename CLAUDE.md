# SEMinR Issue Triage

This repo tracks issue triage, release planning, and development priorities for the [seminr](https://github.com/sem-in-r/seminr) R package.

## Documents

- `chore-triage.md` — Main development queue (priorities, bugs, features, backlog)
- `develop-upcoming.md` — PRs merged to develop, pending next release
- `releases/` — Archived release history and closed issues

## Workflow

1. **Triage here** — prioritize, investigate, plan (with read access to seminr source via CLAUDE.local.md)
2. **Implement in seminr** — switch to a seminr worktree for code changes, tests, PRs

## Accessing the SEMinR Codebase

Each maintainer configures `CLAUDE.local.md` (gitignored) to point to their local seminr checkout. This enables Claude Code to read source files, grep functions, check git history, and run tests — all from this repo's context.

Example git commands using the seminr repo:
```bash
git -C /path/to/seminr log --oneline -20
git -C /path/to/seminr diff develop..feature-branch
```
