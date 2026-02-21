---
name: triage-update
description: Sync seminr-issues tracking documents with the current state of the seminr GitHub repo.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash(gh *), Bash(git -C *), Bash(npx markdownlint-cli *)
---

# Triage Update

Reconcile the three tracking documents (`triage.md`, `next-release.md`,
`releases/v*.md`) with the live state of the seminr GitHub repo.

All updates are local only — nothing is committed or pushed.

---

## Phase 1: Prerequisites

1. **Read `CLAUDE.local.md`** in the project root to get the local
   seminr repo path. If it does not exist, tell the user to run
   `/repo-setup` first and stop.

2. **Verify GitHub CLI auth**: Run `gh auth status`. If not
   authenticated, tell the user and stop.

3. **Read `CLAUDE.md`** to refresh on repo conventions (link formatting, table style,
   markdownlint requirement, CRAN cadence policy).

---

## Phase 2: Gather Data

Read all three tracking documents and query GitHub/git in parallel.

### Documents to read

- `triage.md`
- `next-release.md`
- All files matching `releases/v*.md`

**Extract the "Updated" date** from each document's front matter. Use the
oldest date as `SINCE_DATE` to scope the GitHub queries below. This avoids
fetching years of irrelevant history and keeps context lean.

### GitHub API queries (use `gh` CLI against `sem-in-r/seminr`)

Run these in parallel where possible. Use `SINCE_DATE` (from document
"Updated" dates above) to scope queries and avoid fetching years of history:

```bash
# Open issues (all — no date filter needed)
gh issue list -R sem-in-r/seminr \
  --state open --limit 200 \
  --json number,title,labels,state,createdAt,updatedAt

# Issues closed since last update
gh issue list -R sem-in-r/seminr \
  --state closed --limit 200 \
  --search "closed:>SINCE_DATE" \
  --json number,title,labels,state,closedAt,stateReason

# Open PRs (all — no date filter needed)
gh pr list -R sem-in-r/seminr \
  --state open \
  --json number,title,author,state,baseRefName,\
headRefName,createdAt,updatedAt,labels

# PRs merged since last update
gh pr list -R sem-in-r/seminr \
  --state merged --limit 100 \
  --search "merged:>SINCE_DATE" \
  --json number,title,author,mergedAt,baseRefName,\
headRefName,labels

# PRs closed WITHOUT merge since last update
# (--state closed includes merged; use --search to exclude them)
gh pr list -R sem-in-r/seminr \
  --limit 50 \
  --search "is:pr is:unmerged is:closed closed:>SINCE_DATE" \
  --json number,title,author,closedAt,baseRefName,\
state,labels
```

### Git queries (use local seminr repo path from CLAUDE.local.md)

```bash
# All release tags with dates (no prefix filter — tags may or may not
# have a 'v' prefix, e.g. "v2.4.2" vs "2.4.0")
git -C <SEMINR_PATH> tag -l \
  --sort=-creatordate \
  --format='%(refname:short) %(creatordate:short)'

# Recent commits on develop (last 60 days)
git -C <SEMINR_PATH> log develop \
  --oneline --since='60 days ago' --first-parent

# Recent commits on master (last 60 days)
git -C <SEMINR_PATH> log master \
  --oneline --since='60 days ago' --first-parent
```

---

## Phase 3: Detect Changes

Compare document contents against GitHub/git data. Track every change you intend
to make. Organize findings into these categories:

### 3a. Issues

- **Newly closed**: Issues listed as open in
  `triage.md` that are now closed on GitHub. Note the
  close reason (fixed by PR, wontfix, not-a-bug, duplicate).
- **Newly opened**: Open issues on GitHub not tracked anywhere
  in the three documents. These are candidates for the temporary
  "New Issues" section.
- **State mismatches**: Issues whose status or notes in the docs don't match GitHub
  (e.g., listed as "Open" but now closed, or vice versa).

### 3b. PRs

- **Newly merged to develop**: Merged PRs with `baseRefName=develop` not yet listed
  in `next-release.md` "PRs Merged to Develop" table.
- **Newly merged to master**: Merged PRs with `baseRefName=master` not yet tracked
  in the release files — these may indicate infrastructure or release PRs.
- **PR state changes**: PRs listed as "Open" in docs that are
  now merged or closed. PRs listed in "PRs Under Review" that
  have been merged or closed.
- **Newly closed (unmerged)**: PRs closed without merging —
  candidates for the "Closed PRs" section in the release archive.
- **New open PRs**: Open PRs on GitHub not tracked in any document.

### 3c. Releases

- **New release tags**: Tags in git not yet having a corresponding
  `releases/v*.md` file.
- **CRAN cadence check**: If a new release is detected, calculate days since the
  previous release tag. Warn if fewer than 45 days.

### 3d. next-release.md reset detection

- If a new release tag exists that is newer than the "Base version" in
  `next-release.md`, then the release has shipped and this file needs a reset:
  archive the old content to the release file, then start fresh.

If no changes are detected in any category, report "No changes detected —
documents are up to date" and stop.

---

## Phase 4: Apply Updates

Apply changes in this order. For each document, check "already tracked?" before
adding anything (idempotency). Only remove items confirmed closed/merged on GitHub.

### 4a. Release archive (`releases/v*.md`)

If a new release tag is detected:

1. Create a new file `releases/v<version>.md` using the format from the
   most recent existing release file as a template. Include:
   - Release metadata (version, date, CRAN link if applicable)
   - PRs included (from the old `next-release.md` "PRs Merged to Develop")
   - Issues closed on release
2. Move any newly closed-without-code-fix issues (wontfix, duplicate, not-a-bug)
   to the "Closed Issues (not bugs)" section, with the close reason and date.
3. Move any newly closed (unmerged) PRs to the appropriate "Closed PRs" subsection
   (Superseded, Stale, or Community), with notes.

If no new release, still update the existing release file:

- Add newly closed non-bug issues to "Closed Issues (not bugs)"
  with reason and date.
- Add newly closed unmerged PRs to the appropriate "Closed PRs" subsection.
- Add any newly merged infrastructure PRs (merged to master, not develop) to
  "Infrastructure" section.

### 4b. `next-release.md`

If a release reset is needed (new tag detected):

1. Clear the "PRs Merged to Develop" and "Issues to Close on Release" tables.
2. Update "Base version" to the new release version.
3. Update "Updated" date to today.
4. Update the related-documents links if the release filename changed.

Then, regardless of reset:

1. **Add new merged-to-develop PRs** to the
   "PRs Merged to Develop" table. Use this row format:
   `| [**#NNN**](url) | [#NNN](url) (desc) | @author | date | notes |`
   Link fixed issues in "Fixes"; use `--` if none.
2. **Update "Issues to Close on Release"**: Add issues fixed by newly merged PRs.
   Cross-reference the PR's linked issues from GitHub.
3. **Sync "PRs Under Review"**: Remove PRs that have been merged or closed.
   Add new open PRs targeting develop that aren't listed elsewhere.
4. Update "Updated" date to today.

### 4c. `triage.md`

1. **Remove closed issues** from all sections. For issues fixed by merged PRs,
   they should already be tracked in `next-release.md`. For non-bug closures,
   they should be in the release archive.
2. **Update PR sections**:
   - "PRs Ready to Review": sync with open PRs from GitHub.
   - "Experimental PRs": remove PRs that have been merged or closed.
   - "Candidates for Closing > Stale PRs": remove closed/merged PRs.
3. **Update issue clusters** in the "Reference: Issue Clusters" section:
   - Move newly closed issues from "Open" to "Fixed in develop" or "Recently closed".
   - Remove issues that no longer exist or are closed.
   - Add notes about newly merged PRs that affect the cluster.
4. **New untriaged issues**: If there are open GitHub issues not tracked in any
   document, append them to a temporary section:

   ```markdown
   ---

   ## New Issues (Not Yet Triaged)

   The following issues were found on GitHub but are not yet categorized.
   Move them to the appropriate section above, then delete this section.

   | Issue | Title | Opened | Labels |
   | --- | --- | --- | --- |
   | [**#NNN**](url) | Title text | YYYY-MM-DD | label1, label2 |
   ```

   If this section already exists, append new issues to it (don't duplicate).
5. **Recount the summary table** at the top. Update each column:
   - "Current Version": latest release tag
   - "PRs to Review": count of open PRs in "PRs Ready to Review"
   - "Merged (pending release)": count and link to next-release.md
   - "Experimental": count of experimental PRs
   - "Ready to Work": count of items in "Ready to Work On" subsections
   - "Needs Investigation": count of items in "Needs Investigation"
   - "Backlog": approximate count (use `NN+` format)
6. Update "Updated" date to today.

---

## Phase 5: Verify and Report

### Markdownlint

Run markdownlint on every modified `.md` file:

```bash
npx markdownlint-cli <file1> <file2> ...
```

The repo has a `.markdownlint.json` config that disables MD013 (line-length)
entirely, since this repo's markdown is URL-heavy (tables, issue clusters,
release notes) and the 80-char limit is impractical.

If violations are found, fix them and re-run until clean. Common fixes:

- Trailing spaces
- Multiple blank lines
- Missing blank line before/after headings or lists
- Inconsistent list markers

### Change summary

Output a clear summary of all changes made, organized by document:

```text
## Triage Update Summary

### next-release.md
- Added PR #NNN (description)
- Removed PR #NNN from "PRs Under Review" (now merged)
- ...

### triage.md
- Removed #NNN (closed as wontfix)
- Added 3 new untriaged issues (#NNN, #NNN, #NNN)
- Updated summary table counts
- ...

### releases/vX.Y.Z.md
- Created new release archive for vX.Y.Z
- ...
  (or: No changes)

### Warnings
- CRAN cadence: vX.Y.Z released only NN days after vA.B.C (< 45 day threshold)
  (only if applicable)
```

End with: **"Changes are local only — not committed."**

Then suggest: **"Run `/triage-next` to refresh recommendations based
on the updated state."**
