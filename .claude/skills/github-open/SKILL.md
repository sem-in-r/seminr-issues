---
name: github-open
description: Open a seminr GitHub resource (PR, issue, branch, release, commit, etc.) by number, name, or qualified reference. Outputs a clickable link.
allowed-tools: Bash(gh issue view *), Bash(gh pr view *), Bash(gh release view *), Bash(gh api *)
---

# GitHub Open

Output a bare clickable link to a resource on the `sem-in-r/seminr` GitHub repo.

The user's argument is passed as `$ARGUMENTS`.

## Rules

- Do NOT output any commentary, explanation, or narration.
- The ONLY output should be the bare URL (or a short error if not found).

## Parsing

The argument may be a bare value or a qualified `<type> <value>` pair (e.g., `issue #394`, `pr 42`, `branch feat-foo`, `release v2.4.2`, `commit abc123`). Strip any `#` prefix from numbers.

## Resolution

Base URL: `https://github.com/sem-in-r/seminr`

| Qualifier | URL pattern | Notes |
|-----------|-------------|-------|
| `pr` | Use `gh pr view <N> --repo sem-in-r/seminr --json url -q .url` | |
| `issue` | Use `gh issue view <N> --repo sem-in-r/seminr --json url -q .url` | |
| `branch` | `<base>/tree/<name>` | |
| `release` / `tag` | `<base>/releases/tag/<value>` | |
| `commit` | `<base>/commit/<sha>` | |
| `action` / `run` | `<base>/actions/runs/<id>` | |
| other qualifier | `<base>/<qualifier>/<value>` | best-effort |

If **no qualifier** is given:

- If the value is a number: try `gh pr view` first, then `gh issue view`.
- Otherwise: treat as a branch name (`<base>/tree/<value>`).

## Output

Print ONLY the bare URL on its own line. No markdown, no labels, no prefix text.
