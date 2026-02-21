---
name: triage-next
description: Recommend which issues, PRs, or features should be processed next based on urgency, user QoL impact, and community engagement.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash(gh *), Bash(git -C *), Bash(npx markdownlint-cli *)
---

# Triage Next

Analyze the current state of the seminr project and recommend what to
work on next. Write recommendations to `triage-next.md`. Prioritize
by urgency, user quality-of-life impact, and community engagement
potential.

---

## Phase 1: Gather Context

### Primary source — local documents

`triage.md` is the curated development queue. Use it as the starting
point rather than re-fetching everything from GitHub. Read these in
parallel:

- `CLAUDE.local.md` — get seminr repo path (stop if missing; tell
  user to run `/repo-setup`)
- `triage.md` — categorized issues, PRs, clusters, backlog
- `next-release.md` — what's already queued for the next release
- `triage-next.md` — previous recommendations (if it exists), to
  inform delta commentary

### Supplementary live signals

Only fetch what the documents don't already capture — engagement
signals and activity pulse:

```bash
# Reaction counts on open issues (community demand signal)
gh issue list -R sem-in-r/seminr \
  --state open --limit 100 \
  --json number,reactionGroups

# Recent issue comments (last 30 days) — active discussions
gh api 'repos/sem-in-r/seminr/issues/comments?sort=created&direction=desc&per_page=50' \
  --jq '.[] | {issue_url, created_at, body: (.body | .[0:80])}'

# Open PR review status (are community PRs waiting?)
gh pr list -R sem-in-r/seminr \
  --state open \
  --json number,author,reviewDecision,updatedAt,isDraft

# Days since last release (CRAN cadence)
git -C <SEMINR_PATH> tag -l --sort=-creatordate \
  --format='%(refname:short) %(creatordate:short)' | head -5
```

---

## Phase 2: Score and Rank

Evaluate items from `triage.md` against the criteria below. You do
NOT need to produce numeric scores — use the criteria as a qualitative
lens and synthesize your judgment into clear recommendations.

### Urgency signals (address soon)

- **Regressions or broken core functionality** — users hitting errors
  in normal workflows
- **PRs awaiting review** — especially community contributions that
  will go stale if ignored; check how long they've been waiting
- **Issues with recent comments** — users actively waiting for a
  response or fix (from the live comments query)
- **Items blocking a release** — if enough fixes are queued on
  develop, consider whether a release is warranted (respect CRAN
  cadence: check days since last release tag)

### User QoL signals (high impact for users)

- **High reaction count** (thumbs-up, +1) — community has voted
- **Multiple issues in the same cluster** — fixing one root cause
  resolves several complaints (use the clusters in triage.md)
- **Frequently asked questions or common stumbling blocks** — things
  that generate repeated issues or confusion
- **Export/reporting gaps** — users often need to get results out of R
  and into papers or reports
- **Better error messages** — reduce support burden and user
  frustration

### Engagement signals (grow the community)

- **Community PRs** — reviewing and merging external contributions
  signals that the project welcomes participation
- **Feature requests with discussion** — issues where multiple users
  have chimed in show demand
- **Quick wins** — small fixes or enhancements that can be shipped
  fast, showing the project is active
- **Documentation gaps** — issues tagged `documentation` that would
  help users self-serve

### Negative signals (deprioritize)

- Stale issues with no recent activity and no user demand
- Large speculative features with no clear design
- Issues that need a reproducible example but none has been provided
- Items already merged and tracked in `next-release.md` (already
  queued — no action needed unless review is required)

---

## Phase 3: Write Recommendations

Write the output to `triage-next.md` in the repo root, overwriting
any previous version. Also display the content to the user.

### Delta awareness

If a previous `triage-next.md` existed, note meaningful changes:

- Items previously flagged as urgent that are still unaddressed
- Items that have been resolved since the last recommendation
- New items that weren't on the radar before

Weave these observations naturally into the recommendations rather
than as a separate section.

### File format

```markdown
# What's Next for SEMinR

**Updated**: YYYY-MM-DD

## Urgent — act now

[1-3 items that need immediate attention, with rationale.
E.g., a community PR going stale, a regression, or a release
decision.]

## High impact — next sprint

[2-4 items that would most improve the user experience or address
common pain points. Explain *why* each matters.]

## Engagement opportunities

[1-3 items that could boost community involvement — quick wins,
community PRs, or popular feature requests.]

## Release readiness

[Assessment of whether the develop branch is ready for a CRAN
release. Include: number of merged PRs, days since last release,
any blockers. If a release is warranted, say so. If not, explain
what's missing.]

## Parking lot

[0-2 items that look important but should be explicitly deferred,
with a brief reason why.]
```

### Writing guidelines

- **Be opinionated**: Don't just list everything — make clear
  recommendations about what to do first and why.
- **Link to issues/PRs**: Use `[#NNN](url)` format for every
  reference.
- **Avoid repeating what's already queued**: If something is already
  merged to develop and tracked in `next-release.md`, don't recommend
  it again unless it needs review.
- **Consider effort vs. impact**: Flag quick wins explicitly.
- **Respect CRAN cadence**: If the last release was fewer than 45 days
  ago, note that a new release should wait.
- **Keep it short**: The file should fit comfortably in one screen.
  Aim for clarity over completeness.

---

## Phase 4: Verify

Run markdownlint on the output file:

```bash
npx markdownlint-cli triage-next.md
```

Fix any violations and re-run until clean.

End by telling the user: **"Recommendations written to triage-next.md."**
