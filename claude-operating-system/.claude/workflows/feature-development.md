# Workflow — Feature Development

> Autonomous end-to-end procedure for shipping a feature. Invoked by `/create-feature`.
> Sequencing matters; do not skip [PM_TOOL] sync or verification.

## 0. Preconditions
- Read [domain-knowledge](../context/domain-knowledge.md) and confirm the feature fits [PROJECT_DOCTRINE]. If it violates doctrine, stop and raise it.
- Verify [MCP/PM-tool](../rules/mcp.md) connectivity.

## 1. Plan
- Restate the feature and acceptance criteria.
- Read affected code (route entry points, libs, components). Identify server vs client boundaries.
- Produce an [implementation plan](../templates/implementation-plan.md). For risky/large work, run [architecture-review](../prompts/architecture-review.md) first.

## 2. Open the [PM_TOOL] card (transition: → [IN_PROGRESS_LIST])
- Search for an existing `[CARD_PREFIX]...` phase card; if none, create one in **[BACKLOG_LIST]**, then move to **[IN_PROGRESS_LIST]**.
- Seed non-technical, outcome-oriented checklist items (build, validate, QA, rollout).

## 3. Build
- Server-first. Add the required route files for your framework: page (server unit), loading (skeleton), error (retry).
- Follow rules: [architecture](../rules/architecture.md), [backend](../rules/backend.md), [frontend](../rules/frontend.md), [ui-ux](../rules/ui-ux.md), [accessibility](../rules/accessibility.md), [security](../rules/security.md), [performance](../rules/performance.md).
- Handle all states: loading / error / empty. Mobile-first; touch targets ≥44px.
- **Update the [PM_TOOL] checklist as each item completes** — don't batch at the end.

## 4. Verify
- Run the [QA checklist](../checklists/qa.md) and [accessibility checklist](../checklists/accessibility.md).
- [TYPECHECK_CMD], [LINT_CMD], [BUILD_CMD]. Behavioral check in the running app.
- Add/extend [TEST_FRAMEWORK] coverage for doctrine-critical paths.

## 5. Sync & close (transition: → [REVIEW_LIST])
- Tick remaining [PM_TOOL] items; add a short progress comment; move card to **[REVIEW_LIST]** (never beyond).
- Record new decisions in [memory/decisions.md](../memory/decisions.md), new debt in [tech-debt.md](../memory/tech-debt.md).
- Prepare a PR using the [PR template](../templates/pr-template.md). **Commit/push only if the user asks.**

## Update behavior
If scope grows mid-build, add [PM_TOOL] checklist items immediately and note it in the plan. Never let [PM_TOOL] drift from reality.
