# What's Next for SEMinR

**Updated**: 2026-02-21

## Urgent — act now

1. **Review community PR [#394](https://github.com/sem-in-r/seminr/pull/394)**
   (custom confidence levels for plot). @Marwolaeth submitted this and
   the maintainer acknowledged it on Feb 18 but hasn't reviewed in
   detail yet. Community PRs go stale quickly — prioritize a thorough
   review and either merge or give actionable feedback within the next
   week.

2. **Close stale candidates**

## High impact — next sprint

1. **[#364](https://github.com/sem-in-r/seminr/issues/364)
   — `all_loc_non_int_items()` bug**. Filed Aug 2025, this is an
   internal function issue that could affect model specification
   silently. Investigate and fix before it bites more users. Likely a
   quick fix once diagnosed.

2. **[#375](https://github.com/sem-in-r/seminr/issues/375) +
   [#136](https://github.com/sem-in-r/seminr/issues/136) — export
   results to file**. Users consistently ask for a way to get SEMinR
   results into papers and reports. A recent comment (Jan 2026) on #375
   shows ongoing demand. Designing an `export_results()` utility would
   address both issues and the broader export/reporting cluster
   ([#372](https://github.com/sem-in-r/seminr/issues/372),
   [#141](https://github.com/sem-in-r/seminr/issues/141)).

3. **[#348](https://github.com/sem-in-r/seminr/issues/348) — duplicate
   paths in `plot()`**. A visible bug when a construct is defined twice.
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

3. **Quick win: close resolved issues**. Five issues
   ([#318](https://github.com/sem-in-r/seminr/issues/318),
   [#299](https://github.com/sem-in-r/seminr/issues/299),
   [#205](https://github.com/sem-in-r/seminr/issues/205),
   [#327](https://github.com/sem-in-r/seminr/issues/327),
   [#386](https://github.com/sem-in-r/seminr/issues/386)) are fixed on
   develop and waiting for release. Comment on each noting that the fix
   is on develop and will ship with the next CRAN release, so users know
   they can install the dev version now.

## Release readiness

- **Last release**: v2.4.2 on 2026-02-18 (3 days ago)
- **Merged to develop since then**: 6 PRs (#395, #396, #384, #397,
  #398, #399) — strong foundation accumulating
- **Earliest next release**: ~early April 2026 (respecting CRAN's
  1-2 month cadence)
- **Blockers**: None yet
- **Recommendation**: No release action needed now. Use the next 6
  weeks to review PR #394, fix a few moderate-priority bugs (#364,
  #348, #262), and potentially land an `export_results()` feature.
  That would make for a compelling v2.5.0.

## Parking lot

1. **[#110](https://github.com/sem-in-r/seminr/issues/110) —
   categorical variable support**. Long-standing request but requires
   significant design work. Defer until a clear design and use case
   is documented.

2. **[#90](https://github.com/sem-in-r/seminr/issues/90) — bootstrap
   indirect effects**. Important mediation feature but complex to
   implement correctly. Worth scoping after the moderate-priority bugs
   are cleared.
