# Workflow — Release Process

> End-to-end release procedure. Invoked by `/release`. Wraps [deployment](deployment.md)
> with versioning, changelog, and tracking. Never push or deploy without user approval.

## 1. Freeze & gate
- Confirm the set of changes going out. Run the [pre-release checklist](../checklists/pre-release.md) — QA, accessibility, and security gates must all pass. Stop on blockers.

## 2. Changelog
- Generate the entry with the [changelog template](../templates/changelog.md) from merged work since the last release (`git log`, merged PRs). Group by Added / Changed / Fixed / Security. Keep it user-facing.

## 3. Version & branch
- Bump version per [git rules](../rules/git.md) on a release branch. Tag only when the user approves.

## 4. Deploy
- Execute the [deployment workflow](deployment.md). Confirm production intent explicitly.

## 5. Verify in production
- Run post-deploy smoke (see deployment §5). Report results honestly.

## 6. Track & record
- Move all included [PM_TOOL] cards to **[REVIEW_LIST]** (never beyond, never archive); add a release comment per card.
- Update [memory/roadmap.md](../memory/roadmap.md) (shipped items) and [memory/decisions.md](../memory/decisions.md) (any release-time calls).

## Rollback
- If production verification fails: roll back immediately, document in [memory/known-issues.md](../memory/known-issues.md), notify the user, and do not mark the release complete.
