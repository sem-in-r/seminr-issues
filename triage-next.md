# What's Next for SEMinR

**Updated**: 2026-02-21

## Urgent — act now

1. **Review community PR [#394](https://github.com/sem-in-r/seminr/pull/394)**
   (custom confidence levels for plot). @Marwolaeth submitted this on
   Feb 17 and the maintainer acknowledged it the next day but hasn't
   reviewed in detail yet. It's been 4 days — community PRs go stale
   quickly. Prioritize a thorough review and either merge or give
   actionable feedback this week. *(Carried forward from last
   recommendation — still waiting.)*

## High impact — next sprint

1. **[#364](https://github.com/sem-in-r/seminr/issues/364)
   — `all_loc_non_int_items()` bug**. Filed Aug 2025, this internal
   function issue could affect model specification silently. Likely a
   quick fix once diagnosed.

2. **[#375](https://github.com/sem-in-r/seminr/issues/375) +
   [#136](https://github.com/sem-in-r/seminr/issues/136) — export
   results to file**. Users consistently ask for a way to get SEMinR
   results into papers and reports. A Jan 2026 comment on #375 shows
   ongoing demand. An `export_results()` utility would address both
   issues and the broader export/reporting cluster
   ([#372](https://github.com/sem-in-r/seminr/issues/372),
   [#141](https://github.com/sem-in-r/seminr/issues/141)).

3. **[#348](https://github.com/sem-in-r/seminr/issues/348) — duplicate
   paths in `plot()`**. Visible bug when a construct is defined twice.
   Plot issues are high-visibility because every user sees the output.

4. **[#262](https://github.com/sem-in-r/seminr/issues/262) — Ten Berge
   fails on non-numeric data**. Missing data type check — should be a
   straightforward guard clause with a clear error message.

## Engagement opportunities

1. **Merge or advance PR #394** (see Urgent above). Merging a community
   contribution sends a strong signal that the project welcomes outside
   contributors.

2. **Issue templates are live** (PR #399 merged). Now that bug report
   and feature request templates exist, monitor incoming issues for
   improved quality and link to the templates when asking reporters for
   more detail.

3. **Comment on develop-fixed issues**. Five issues
   ([#318](https://github.com/sem-in-r/seminr/issues/318),
   [#299](https://github.com/sem-in-r/seminr/issues/299),
   [#205](https://github.com/sem-in-r/seminr/issues/205),
   [#327](https://github.com/sem-in-r/seminr/issues/327),
   [#386](https://github.com/sem-in-r/seminr/issues/386)) are fixed on
   develop and waiting for release. Comment on each noting the fix is
   available on the dev branch and will ship with the next CRAN release,
   so users know they can install from GitHub now.

## Release readiness

- **Last release**: v2.4.2 on 2026-02-18 (3 days ago)
- **Merged to develop since then**: 6 PRs (#395, #396, #384, #397,
  #398, #399) — strong foundation accumulating
- **Earliest next release**: ~early April 2026 (respecting CRAN's
  1-2 month cadence)
- **Blockers**: None
- **Recommendation**: No release action needed now. Use the next 4-6
  weeks to review PR #394, fix moderate-priority bugs (#364, #348,
  #262), and potentially land an `export_results()` feature. That
  would make for a compelling v2.5.0.

## Parking lot

1. **[#110](https://github.com/sem-in-r/seminr/issues/110) —
   categorical variable support**. Long-standing request but requires
   significant design work. Defer until a clear design and use case
   is documented.

2. **[#90](https://github.com/sem-in-r/seminr/issues/90) — bootstrap
   indirect effects**. Important mediation feature but complex to
   implement correctly. Worth scoping after the moderate-priority bugs
   are cleared.

## Changes since last recommendation

- **Resolved**: Stale candidates (#209, #217) have been closed —
  previously flagged as urgent, now done.
- **Unchanged**: PR #394 remains unreviewed. All high-impact items
  (#364, #375+#136, #348, #262) still unaddressed.
- **No new items**: No new issues or PRs since the last recommendation.
