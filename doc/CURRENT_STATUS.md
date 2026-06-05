# Current Project Status

Last updated: 2026-06-04

## In Progress

- [ ] Release 0.3.0 candidate (PR #32) — pending CI rerun after merge with master

## Recently Completed

- [x] Adopt GitHub Flow; retire `develop` as base branch (ADR-006, PR #34)
- [x] Branch protection on `master`; CI job renamed `Unit Tests` (no emoji) (PR #33)
- [x] Release 0.2.1 published (PR #29)
- [x] Snooze cooldown for "remind me later" and dismiss (#30) — shipping in 0.3.0
- [x] Trigger counter reset on engagement (positive/negative) — shipping in 0.3.0
- [x] Handle OS review not available (`ReviewFlowResult.reviewNotAvailable`) — shipping in 0.3.0
- [x] Pre-emptive snooze safety net for app kills during dialog — shipping in 0.3.0
- [x] Fix debug mode — only enables logging, never bypasses pipeline stages
- [x] ADR-005 updated with GitHub CLI conventions
- [x] Rename docs/ to doc/ and add publish validation to CI
- [x] Prevent multiple dialogs when `logEvent()` is called concurrently (#28, PR #27)
- [x] Context-First Development (CFD) methodology (#26)
- [x] Debug dashboard widget and `getDebugSnapshot()` (#24)

## Open Issues

- #4 Bottom sheet dialog variant (feature, tier-1)
- #11 Widget tests for default dialog adapters (testing, tier-2)
- #19 Ship `SharedPreferencesStorageAdapter` as companion package (enhancement, tier-2)
- #14 Theming support for default dialogs (enhancement, tier-3)

## Known Issues

- None currently tracked

## Next Priorities

1. Merge PR #32 → tag and publish 0.3.0 to pub.dev
2. Bottom sheet dialog variant (#4) — tier-1
3. Widget tests for default dialog adapters (#11) — tier-2
4. SharedPreferencesStorageAdapter companion package (#19) — tier-2
