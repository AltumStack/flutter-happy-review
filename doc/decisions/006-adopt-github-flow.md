# ADR-006: Adopt GitHub Flow

## Status

Accepted

## Date

2026-06-04

## Context

ADR-005 codified a Git Flow–style process: short-lived feature branches off `develop`, with `release/x.y.z` branches cut from `develop` and merged into `master` for publication. In practice this project is maintained by a single person, releases happen frequently, and the `develop` integration branch added overhead without delivering its main benefit (parallel feature integration ahead of a release window).

Recent reality reinforces this: branch protection has now been applied to `master` only, the working branch in this repo is `master`, and PR #33 already merged directly to `master` without using `develop`. Keeping `develop` documented as the base branch would contradict the live protection rules and the actual flow.

## Decision

Adopt GitHub Flow:

1. `master` is the single long-lived branch and the source of truth.
2. Branch off `master` for every change using the prefixes from ADR-005 (`fix/`, `feature/`, `chore/`, `ci/`, `docs/`, `release/`).
3. Open a PR back to `master`. CI (`Unit Tests`) must be green and at least 1 review must approve before merge.
4. Releases are cut directly from `master`: bump version, update CHANGELOG/README on a `release/x.y.z` branch, PR to `master`, tag the merge commit, publish to pub.dev.
5. The `develop` branch is retired. It will be deleted from the remote once any in-flight branches based on it have been rebased onto `master`.

The PR metadata rules from ADR-005 still apply (template, project link, labels carried from linked issue), with two corrections:

- **Base branch** is `master` (was `develop`).
- **PR assignee** is `albertomarturelo` (was the non-existent login `AMarturelo`).

## Alternatives Considered

1. **Keep Git Flow as documented in ADR-005** — Rejected. The `develop` branch added a merge step without a corresponding benefit for a solo maintainer with frequent releases, and the divergence between documented process and actual practice was a source of confusion.
2. **Trunk-based development with feature flags** — Rejected. The library is small enough that PR-gated review on `master` is sufficient, and feature-flag infrastructure would be over-engineering at the current scale.
3. **Release branches as long-lived stabilization branches** — Rejected. Hotfixes to released versions can be handled by tagging from `master` or by short-lived `release/x.y.z` branches; no need to keep them alive between releases.

## Consequences

- One less integration step per change; faster path from branch to release.
- `master` must always be releasable, so PRs need to be small and CI must be trustworthy. The `Unit Tests` required status check enforces the second part.
- Branch protection on `master` is now the single gate. There is no second-chance review on a downstream merge to `master` — every PR is the production merge.
- Documentation in `CLAUDE.md` and `CONVENTIONS.md` updated to reflect `master` as the base branch.
- ADR-005 is marked Superseded for the base-branch and assignee sections; its label, template, and branch-naming rules remain in force.
