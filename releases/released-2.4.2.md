# SEMinR Completed Issues & PRs

**Repository**: [sem-in-r/seminr](https://github.com/sem-in-r/seminr)
**Purpose**: Archive of closed issues, merged PRs, and past releases.

Related documents:

- [issues-triage.md](../issues-triage.md) -- open issues and development queue
- [develop-upcoming.md](../develop-upcoming.md) -- PRs merged to develop, pending next release

---

## v2.4.2 (2026-02-19)

Released to CRAN via v2.4.1 ([PR #392](https://github.com/sem-in-r/seminr/pull/392)) then v2.4.2 (test consolidation for CRAN timing). Tagged [v2.4.2](https://github.com/sem-in-r/seminr/releases/tag/v2.4.2).

### PRs included

| PR | Fixes | Author | Notes |
| --- | --- | --- | --- |
| [**#379**](https://github.com/sem-in-r/seminr/pull/379) | [#377](https://github.com/sem-in-r/seminr/issues/377) (VIF output) | @soumyaray | Fix vif_items named list structure |
| [**#383**](https://github.com/sem-in-r/seminr/pull/383) | [#369](https://github.com/sem-in-r/seminr/issues/369), [#373](https://github.com/sem-in-r/seminr/issues/373) (HOC summary) | @soumyaray | Fix + linting for HOC summary |
| [**#388**](https://github.com/sem-in-r/seminr/pull/388) | PLSpredict parallel testing | @soumyaray | Fix parallel worker behavior on local macOS |
| [**#380**](https://github.com/sem-in-r/seminr/pull/380) | CI workflow | @soumyaray | Fix GitHub Actions for Ubuntu 24.04 |
| [**#389**](https://github.com/sem-in-r/seminr/pull/389) | [#226](https://github.com/sem-in-r/seminr/issues/226) (Plot symbols) | @soumyaray | Fix BMP Greek letters for lambda, beta, gamma in plot exports; capital R-squared |
| [**#390**](https://github.com/sem-in-r/seminr/pull/390) | [#347](https://github.com/sem-in-r/seminr/issues/347) (predict_pls rownames) | @soumyaray | Regression test confirming fix from PR #368 |

### Issues closed

| Issue | Title | Fixed By |
| --- | --- | --- |
| [**#369**](https://github.com/sem-in-r/seminr/issues/369) | summary() regression in v2.3.7 | PR #383 |
| [**#373**](https://github.com/sem-in-r/seminr/issues/373) | HOC summary undefined columns | PR #383 |
| [**#347**](https://github.com/sem-in-r/seminr/issues/347) | predict_pls subscript error | PR #368 (regression test in PR #390) |
| [**#298**](https://github.com/sem-in-r/seminr/issues/298) | predict_pls() rownames error | PR #368 |
| [**#377**](https://github.com/sem-in-r/seminr/issues/377) | VIF output structure inconsistent | PR #379 |
| [**#226**](https://github.com/sem-in-r/seminr/issues/226) | Lambda symbol not rendered | PR #389 |

---

## v2.4.0 (2026-02-04)

Released to master via [PR #385](https://github.com/sem-in-r/seminr/pull/385).

---

## Earlier Releases

### v2.3.1

| Issue | Title | Fixed By |
| --- | --- | --- |
| [**#240**](https://github.com/sem-in-r/seminr/issues/240) | summary() fails with factor column | PR #285 |

---

## Closed Issues (not bugs -- resolved without code fix)

| Issue | Title | Reason | Closed |
| --- | --- | --- | --- |
| [**#353**](https://github.com/sem-in-r/seminr/issues/353) | summary() subscript out of bounds | Closed -- model misspecification | 2026-02-03 |
| [**#329**](https://github.com/sem-in-r/seminr/issues/329) | Bootstrap error | Resolved by reporter -- haven package interference, not seminr | 2026-02-21 |
| [**#150**](https://github.com/sem-in-r/seminr/issues/150) | Repeated indicators HOC | Closed as wontfix | 2026-02-21 |
| [**#223**](https://github.com/sem-in-r/seminr/issues/223) | semPlot not installing | External dependency, not seminr | 2026-02-21 |

---

## Infrastructure (merged to master)

| Item | Fixed By | Merged |
| --- | --- | --- |
| Issue templates (bug report + feature request) | PR #399 + PR #400 | 2026-02-21 |

---

## Closed PRs

### Superseded

| PR | Title | Superseded By |
| --- | --- | --- |
| [**#374**](https://github.com/sem-in-r/seminr/pull/374) | Fixed summary error (missing data + HOC) | PR #383 |
| [**#393**](https://github.com/sem-in-r/seminr/pull/393) | Custom confidence levels for plotting | PR #394 |

### Stale PRs (closed without merge)

| PR | Title | Reason | Closed |
| --- | --- | --- | --- |
| [**#313**](https://github.com/sem-in-r/seminr/pull/313) | Issue templates update | Superseded by PR #399 + #400 | 2026-02-21 |
| [**#220**](https://github.com/sem-in-r/seminr/pull/220) | Bootstrap significance | Superseded by PR #358 (Wald test) | 2026-02-21 |

### Community PRs (closed without merge)

| PR | Author | Title | Notes |
| --- | --- | --- | --- |
| [**#391**](https://github.com/sem-in-r/seminr/pull/391) | @Marwolaeth | Fix column selection in report_missing | Closed without merge |
