# Checklist — Pre-Release Gate

> Master gate before cutting a release. Run during the [release process](../workflows/release-process.md).
> A single unchecked blocker stops the release.

## Quality gates (all must pass)
- [ ] [QA checklist](qa.md) — green
- [ ] [Accessibility checklist](accessibility.md) — green
- [ ] [Security review](security-review.md) — green
- [ ] [Deployment checklist](deployment.md) — prepared

## Doctrine integrity
- [ ] [PROJECT_DOCTRINE] still holds — no core product principle violated
- [ ] Any AI behavior stays within its defined role + gating threshold
- [ ] Primary/manager views respect the look-and-feel + information-priority locks
- [ ] Tenant isolation verified across roles ([ADMIN_ROLE] / [MANAGER_ROLE] / [EDITOR_ROLE] / [VIEWER_ROLE])

## Release artifacts
- [ ] [Changelog](../templates/changelog.md) entry written (user-facing)
- [ ] Version bumped per [git rules](../rules/git.md)
- [ ] All included work merged; no orphaned WIP

## Tracking
- [ ] Every included [PM_TOOL] card ready to move to **[REVIEW_LIST]**
- [ ] [memory/roadmap.md](../memory/roadmap.md) and [decisions.md](../memory/decisions.md) reflect what's shipping
- [ ] Open product decisions (see `[DOCS_DIR]/technical-spec`) that block this release are resolved or explicitly deferred

## Sign-off
- [ ] User has approved the deploy/push (never deploy or push unprompted)
