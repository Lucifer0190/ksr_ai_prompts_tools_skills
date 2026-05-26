---
description: Build a feature end-to-end following the [PROJECT_NAME] feature-development workflow
argument-hint: <feature description>
---

# /create-feature

Implement the feature described in `$ARGUMENTS` by executing
[.claude/workflows/feature-development.md](../workflows/feature-development.md) start to finish.

## Execution flow
1. **Understand & plan.** Restate the feature, check doctrine fit ([domain-knowledge](../context/domain-knowledge.md)), read affected code. Produce an [implementation plan](../templates/implementation-plan.md).
2. **[PM_TOOL].** Per [trello rules](../rules/trello.md): find or create the phase card (`[CARD_PREFIX]...`), add it to [BACKLOG_LIST], move to [IN_PROGRESS_LIST], seed non-technical checklist items.
3. **Build.** Follow all `@`-imported rules (architecture, backend, frontend, ui-ux, accessibility, security). Server-first; required route files (`page`/`loading`/`error`) and all UI states.
4. **Verify.** Run the [QA checklist](../checklists/qa.md): [TYPECHECK_CMD], [LINT_CMD], build, behavioral check. Add e2e for doctrine-critical paths.
5. **Sync & finish.** Tick [PM_TOOL] checklist items, add a progress comment, move card to [REVIEW_LIST]. Record any new decision/debt in [memory](../memory/). Prepare a PR via the [PR template](../templates/pr-template.md) — commit/push only if the user asks.

## Expected output
- Working, type-checked, lint-clean feature.
- Updated [PM_TOOL] card ([IN_PROGRESS_LIST] → [REVIEW_LIST]) with ticked checklist + progress comment.
- A PR description (not pushed unless requested).
- Honest verification report (what passed, what was skipped).
