# SEMinR Development Queue

**Repository**: [sem-in-r/seminr](https://github.com/sem-in-r/seminr)
**Updated**: 2026-02-21
**Issue closing policy**: Fixed in develop, close on release

Related documents:
- [develop-upcoming.md](develop-upcoming.md) — PRs merged to develop, issues to close on next release
- [released-2.4.2.md](released-2.4.2.md) — release history, closed issues, archived PRs

## Summary

| Current Version | PRs to Review | Merged (pending release) | Experimental | Ready to Work | Needs Investigation | Backlog |
| --------------- | ------------- | ------------------------ | ------------ | ------------- | ------------------- | ------- |
| v2.4.2 | 1 (community) | [5 PRs](develop-upcoming.md) | 2 PRs | 5 moderate | 4 issues | 20+ |

---

## Immediate Actions

### PRs Ready to Review

| PR | Author | Status | Notes |
| --- | --- | --- | --- |
| [**#394**](https://github.com/sem-in-r/seminr/pull/394) | @Marwolaeth | Open | Enable custom confidence levels for plotting bootstrapped models; community contribution |

---

## Ready to Work On

### Moderate Priority Bugs

| Issue | Title | Status | Notes | Cluster |
| --- | --- | --- | --- | --- |
| [**#364**](https://github.com/sem-in-r/seminr/issues/364) | all_loc_non_int_items() issue | Open | Internal function; recent (2025-08) | -- |
| [**#341**](https://github.com/sem-in-r/seminr/issues/341) | HTMT Inf error in bootstrap | Open | Small sample sizes; low engagement | bootstrap |
| [**#348**](https://github.com/sem-in-r/seminr/issues/348) | Duplicate paths in plot() | Open | Construct defined twice | plot |
| [**#262**](https://github.com/sem-in-r/seminr/issues/262) | Ten Berge fails non-numeric | Open | Missing data type check | -- |
| [**#213**](https://github.com/sem-in-r/seminr/issues/213) | save_plot() HOC + moderation | Open | Plot export issue | hoc + plot |

### High-Demand Features

| Issue | Title | Status | Notes |
| --- | --- | --- | --- |
| [**#375**](https://github.com/sem-in-r/seminr/issues/375) + [**#136**](https://github.com/sem-in-r/seminr/issues/136) | Export results to file | Open | Combine into `export_results()` |
| [**#90**](https://github.com/sem-in-r/seminr/issues/90) | Bootstrap indirect effects | Open | Core mediation feature |
| [**#110**](https://github.com/sem-in-r/seminr/issues/110) | Categorical variable support | Open | Long-standing request |

---

## Needs Investigation

| Issue | Title | Status | What's Needed |
| --- | --- | --- | --- |
| [**#350**](https://github.com/sem-in-r/seminr/issues/350) | "Bootstrapping keeps running" | Open | Reproducible example needed |
| [**#256**](https://github.com/sem-in-r/seminr/issues/256) | Bootstrapping issue | Open | Tagged `doing` since 2022; check if still relevant |
| [**#339**](https://github.com/sem-in-r/seminr/issues/339) | Near-zero-variance binary | Open | Left open for discoverability; consider documenting as known limitation |
| [**#291**](https://github.com/sem-in-r/seminr/issues/291) | Dissimilar p-values in MGA | Open | Methodology clarification; tagged `documentation` |

---

## Backlog

### Features

| Issue | Title | Notes |
| --- | --- | --- |
| [**#335**](https://github.com/sem-in-r/seminr/issues/335) | Time series bootstrapping | Block bootstrap support |
| [**#326**](https://github.com/sem-in-r/seminr/issues/326) + [**#320**](https://github.com/sem-in-r/seminr/issues/320) | Weighted PLS | Survey weights / post-stratification |
| [**#319**](https://github.com/sem-in-r/seminr/issues/319) | BCa confidence intervals | Bias-corrected bootstrap |
| [**#261**](https://github.com/sem-in-r/seminr/issues/261) | Invariance testing | MICOM support |
| [**#254**](https://github.com/sem-in-r/seminr/issues/254) | Bootstrap reliability CIs | CI for measurement metrics |
| [**#248**](https://github.com/sem-in-r/seminr/issues/248) | Invalid solution warnings | Solution quality checks |
| [**#236**](https://github.com/sem-in-r/seminr/issues/236) | Mediated-moderation | Complex moderation patterns |
| [**#163**](https://github.com/sem-in-r/seminr/issues/163) | Sign indeterminacy | Handle sign flipping in bootstrap |
| [**#160**](https://github.com/sem-in-r/seminr/issues/160) | Tidy CFA/EFA output | Tidyverse compatibility |
| [**#151**](https://github.com/sem-in-r/seminr/issues/151) | GSCA estimation | Alternative method |
| [**#146**](https://github.com/sem-in-r/seminr/issues/146) | as.composite() | Convert reflective to composite |
| [**#145**](https://github.com/sem-in-r/seminr/issues/145) | SRMR fit index | Additional CBSEM fit index |
| [**#134**](https://github.com/sem-in-r/seminr/issues/134) | Construct class names order | Code refactoring |
| [**#55**](https://github.com/sem-in-r/seminr/issues/55) | Model simulation | Monte Carlo support |
| [**#53**](https://github.com/sem-in-r/seminr/issues/53) | MGA improvements | Enhanced multi-group analysis |

### Lower Priority Bugs

| Issue | Title | Notes |
| --- | --- | --- |
| [**#233**](https://github.com/sem-in-r/seminr/issues/233) | fSquared missing for indirect | May be feature not bug |
| [**#250**](https://github.com/sem-in-r/seminr/issues/250) | Bootstrap 1 antecedent, many outcomes | Edge case |
| [**#224**](https://github.com/sem-in-r/seminr/issues/224) | Unfriendly item name errors | Better error messages |
| [**#257**](https://github.com/sem-in-r/seminr/issues/257) | Parallel error reporting | Internal improvement |

---

## Experimental PRs

Low priority explorations -- not actively being addressed.

| PR | Title | Author | Notes |
| --- | --- | --- | --- |
| [**#358**](https://github.com/sem-in-r/seminr/pull/358) | Wald test for bootstrap paths | @soumyaray | Addresses [#141](https://github.com/sem-in-r/seminr/issues/141), [#372](https://github.com/sem-in-r/seminr/issues/372) (p-values) |
| [**#221**](https://github.com/sem-in-r/seminr/pull/221) | Unstandardization features | @soumyaray | Targets `develop` branch |

---

## Candidates for Closing

### Stale PRs (>2 years)

| PR | Title | Decision Needed |
| --- | --- | --- |
| [**#217**](https://github.com/sem-in-r/seminr/pull/217) | Package paper | Evaluate: still want paper? |

### Stale Issues

| Issue | Title | Reason |
| --- | --- | --- |
| [**#209**](https://github.com/sem-in-r/seminr/issues/209) | MKL CRAN test | Old CI issue |
| [**#222**](https://github.com/sem-in-r/seminr/issues/222) | pls_predict HOC error | Likely covered by other HOC fixes |

---

## Reference: Issue Clusters

Understanding these patterns helps prioritize fixes that address multiple issues. Only open issues listed.

### HOC/Higher-Order Construct Issues

- **Open**: [#222](https://github.com/sem-in-r/seminr/issues/222), [#213](https://github.com/sem-in-r/seminr/issues/213)
- **Fixed in develop**: [#299](https://github.com/sem-in-r/seminr/issues/299) + [#205](https://github.com/sem-in-r/seminr/issues/205) -- [PR #396](https://github.com/sem-in-r/seminr/pull/396) merged
- **Pattern**: HOC + bootstrap failures
- **Recommendation**: Review remaining HOC code paths (#222, #213) now that #396 is merged

### Bootstrap Issues

- **Open**: [#350](https://github.com/sem-in-r/seminr/issues/350), [#341](https://github.com/sem-in-r/seminr/issues/341), [#339](https://github.com/sem-in-r/seminr/issues/339), [#256](https://github.com/sem-in-r/seminr/issues/256), [#250](https://github.com/sem-in-r/seminr/issues/250), [#163](https://github.com/sem-in-r/seminr/issues/163)
- **Fixed in develop**: [#318](https://github.com/sem-in-r/seminr/issues/318) -- [PR #395](https://github.com/sem-in-r/seminr/pull/395) merged; [#299](https://github.com/sem-in-r/seminr/issues/299)+[#205](https://github.com/sem-in-r/seminr/issues/205) -- [PR #396](https://github.com/sem-in-r/seminr/pull/396) merged
- **CI**: [PR #397](https://github.com/sem-in-r/seminr/pull/397) adds Windows CI -- bootstrap parallel tests now verified on all 3 platforms
- **Recently closed**: #329 (haven interference, not seminr -- closed 2026-02-21)
- **Pattern**: Many edge cases and environment-specific issues
- **Recommendation**: Two highest-impact bootstrap bugs (#318, #299+#205) now merged; close issues on next release; remaining open items are lower priority

### Export/Reporting Issues

- **Open**: [#375](https://github.com/sem-in-r/seminr/issues/375), [#372](https://github.com/sem-in-r/seminr/issues/372), [#141](https://github.com/sem-in-r/seminr/issues/141), [#136](https://github.com/sem-in-r/seminr/issues/136), [#90](https://github.com/sem-in-r/seminr/issues/90)
- **Pattern**: Users want easy export and complete reporting
- **Recommendation**: Create comprehensive `export_results()` utilities

### Prediction Issues

- **Open**: [#222](https://github.com/sem-in-r/seminr/issues/222)
- **Recommendation**: Add input validation

### Summary Function Issues

- **Open**: [#341](https://github.com/sem-in-r/seminr/issues/341) (HTMT Inf with small samples)
- **Recommendation**: Edge case -- small sample size handling
