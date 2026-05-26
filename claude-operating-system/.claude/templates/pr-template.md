# Template — Pull Request

> Fill and use as the PR body. Keep it reviewer-friendly. Link the [PM_TOOL] card.

```markdown
## Summary
<one paragraph: what changed and why, in plain language>

## [PM_TOOL]
- Card: [CARD_PREFIX]<card title> (<link>) — moved to [REVIEW_LIST]

## Changes
- <bullet per meaningful change>

## Doctrine & rules check
- [ ] Respects [PROJECT_DOCTRINE] (no violation of core product principles)
- [ ] Any AI behavior stays within its defined role + threshold (if AI touched)
- [ ] [VIEWER_ROLE] read-only; unauthorized access returns 404-not-403; tenancy/authz intact
- [ ] loading / error / empty states present
- [ ] Accessible (focus rings, aria, labels) + responsive at 375px

## Verification
- type-check (`[TYPECHECK_CMD]`): <pass/fail>  · lint (`[LINT_CMD]`): <pass/fail>  · build (`[BUILD_CMD]`): <pass/fail>
- Manual/behavioral: <what you observed>
- Tests added/updated: <which paths>

## Notes / follow-ups
<tech debt, decisions, or out-of-scope items — link memory/ entries>

🤖 Generated with [Claude Code](https://claude.com/claude-code)
```
