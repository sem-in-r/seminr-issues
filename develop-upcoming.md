# SEMinR Upcoming Release (develop)

**Repository**: [sem-in-r/seminr](https://github.com/sem-in-r/seminr)
**Base version**: v2.4.2
**Updated**: 2026-02-21
**Issue closing policy**: Issues remain open until fixes are released to CRAN

Related documents:

- [issues-triage.md](issues-triage.md) -- open issues and development queue
- [released-2.4.2.md](releases/released-2.4.2.md) -- release history and archived items

---

## PRs Merged to Develop

| PR | Fixes | Author | Merged | Notes |
| --- | --- | --- | --- | --- |
| [**#395**](https://github.com/sem-in-r/seminr/pull/395) | [#318](https://github.com/sem-in-r/seminr/issues/318) (parallel "no package seminr") | @soumyaray | 2026-02-20 | Propagate `.libPaths()` to workers, shared `setup_parallel_cluster()` helper, remove `seminr::` self-refs |
| [**#396**](https://github.com/sem-in-r/seminr/pull/396) | [#299](https://github.com/sem-in-r/seminr/issues/299) + [#205](https://github.com/sem-in-r/seminr/issues/205) (PLSc + HOC bootstrap) | @soumyaray | 2026-02-20 | Fix `boot_vec_len` miscalculation in error-recovery; rename shadowed `length` variable |
| [**#384**](https://github.com/sem-in-r/seminr/pull/384) | [#386](https://github.com/sem-in-r/seminr/issues/386) (macOS CI failures) | @soumyaray | 2026-02-20 | Switch to PPM repo for macOS; remove macOS-devel from CI matrix; add workflow_dispatch + setup-pandoc@v2 |
| [**#397**](https://github.com/sem-in-r/seminr/pull/397) | -- (CI modernization) | @soumyaray | 2026-02-21 | Add Windows CI, modernize to standard r-lib/actions `check-r-package@v2`, use public RSPM for all platforms |
| [**#398**](https://github.com/sem-in-r/seminr/pull/398) | [#327](https://github.com/sem-in-r/seminr/issues/327) (quadratic interaction error) | @soumyaray | 2026-02-21 | `drop=FALSE` fixes for matrix subset coercion; add `quadratic_term()` convenience function |

---

## Issues to Close on Release

| Issue | Title | Fixed By |
| --- | --- | --- |
| [**#318**](https://github.com/sem-in-r/seminr/issues/318) | PLS Bootstrap error: "no package called seminr" | PR #395 |
| [**#299**](https://github.com/sem-in-r/seminr/issues/299) | bootstrap_model() errors with PLSc + HOC | PR #396 |
| [**#205**](https://github.com/sem-in-r/seminr/issues/205) | PLSc bootstrap errors with HOC | PR #396 |
| [**#327**](https://github.com/sem-in-r/seminr/issues/327) | interaction_term() quadratic error with single IV | PR #398 |
| [**#386**](https://github.com/sem-in-r/seminr/issues/386) | macOS CI failures (pak/CRAN sync) | PR #384 |

---

## PRs Under Review

| PR | Author | Status | Notes |
| --- | --- | --- | --- |
| [**#394**](https://github.com/sem-in-r/seminr/pull/394) | @Marwolaeth | Open | Enable custom confidence levels for plotting bootstrapped models; community contribution |
