---
name: announce
description: Create or update a social media announcement (Facebook/LinkedIn) for SEMinR based on user description. Saves to the announcements directory.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash(git -C *), Bash(gh *)
---

# Announce

Create or update a social media announcement for SEMinR, formatted for
copy-paste into Facebook and LinkedIn.

The user's description is passed as `$ARGUMENTS`. If empty, ask what the
announcement should cover.

---

## Phase 1: Gather Context

### Check for existing announcements

```bash
ls -1 ../announcements/
```

Read any recent announcements to stay consistent with tone and style.

### Check if this is an update

If the user says "update" or references an existing announcement file,
read that file so you can revise it in place.

### Gather supporting details (if needed)

If the announcement is about a release, PR, or issue, pull details:

```bash
# Recent tags/releases
git -C <SEMINR_PATH> tag -l --sort=-creatordate \
  --format='%(refname:short) %(creatordate:short)' | head -5

# PR or issue details
gh pr view <N> --repo sem-in-r/seminr
gh issue view <N> --repo sem-in-r/seminr
```

Read `CLAUDE.local.md` to get the seminr repo path. Also check
`next-release.md` and `triage.md` if release context is needed.

---

## Phase 2: Draft the Announcement

### Output format

Write **plain text** (`.txt`), NOT markdown. The file must be
copy-paste ready for Facebook and LinkedIn with no reformatting needed.

### Style conventions (match existing announcements)

- **ALL-CAPS section headers** with a line of `===` or `---` underneath
- Use `~` as bullet character (preceded by two spaces):
  `  ~ item text here`
- Blank line between sections
- No markdown formatting (no `**bold**`, no `[links](url)`, no `#`
  headers)
- URLs written out in full (bare URLs are fine on social media)
- Keep paragraphs short and scannable — social media readers skim
- Professional but approachable tone — this is an open-source project
  speaking to its user community

### Required sections

Adapt sections to the content, but a typical announcement includes:

```
SECTION HEADER
==============

FACEBOOK / LINKEDIN POST
-------------------------

[Main post body — 1-3 short paragraphs covering the key points.
Lead with the most exciting or important item.]

[Bullet list of details if applicable:]
  ~ detail one
  ~ detail two

[Optional: "Coming next" or "What's ahead" teaser]

[Optional: Community recognition / thank-yous]

Install/update: install.packages("seminr")
GitHub: https://github.com/sem-in-r/seminr


SHORT VERSION
-------------

[Single paragraph, under 280 characters if possible, suitable for a
quick share or tweet-length post. Hit the key headline only.]
```

Not every section is required — tailor to what makes sense for the
content. A bug-fix announcement doesn't need a "Coming next" section.
A community update might not need install instructions.

### Tone guidance

- Lead with what users care about, not internal details
- Use "we" for the team, "you" for the user
- Be specific — name the functions, the fixes, the features
- Avoid jargon that non-R users wouldn't understand (but assume
  the audience knows R and SEM basics)
- End with a clear call to action (update, try it, give feedback)

---

## Phase 3: Write the File

### Filename convention

`MM-DD-YYYY-announce.txt`

Use today's date (from `CLAUDE.local.md` or system date). If updating
an existing file, keep its original filename.

### File location

Write to `../announcements/` (relative to the seminr-issues repo root).

---

## Phase 4: Present to User

Display the full announcement text to the user so they can review it
before copying to social media. Mention the filename and path.

If the user wants changes, update the file in place.
