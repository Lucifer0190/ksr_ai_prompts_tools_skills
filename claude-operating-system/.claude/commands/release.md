---
description: Run the [PROJECT_NAME] release process — verify, changelog, deploy, track
argument-hint: "[version or release name]"
---

# /release

Cut a release (`$ARGUMENTS`) by executing
[.claude/workflows/release-process.md](../workflows/release-process.md) and
[.claude/workflows/deployment.md](../workflows/deployment.md).

## Execution flow
1. **Gate.** Run the [pre-release checklist](../checklists/pre-release.md) — all rule checklists (QA, a11y, security) must pass. Stop on any blocker.
2. **Changelog.** Generate notes with the [changelog template](../templates/changelog.md) from merged work since the last release.
3. **Version & branch.** Per [git rules](../rules/git.md). Never push without explicit user approval.
4. **Deploy.** Follow [deployment checklist](../checklists/deployment.md) ([HOSTING]). Confirm env vars and that [SCHEMA_FILE] has been applied if it changed.
5. **Track & finish.** Move all included [PM_TOOL] cards to **[REVIEW_LIST]** (never beyond). Add a release comment. Update [memory/roadmap.md](../memory/roadmap.md) and [decisions.md](../memory/decisions.md).

## Expected output
- Pre-release gate result (pass/blockers).
- Changelog entry.
- Deploy outcome + post-deploy smoke result.
- [PM_TOOL] + memory updated.

> Releasing publishes outward-facing changes — confirm with the user before deploying or pushing.
