---
description: Turn a sprint goal into a doctrine-aligned plan and [PM_TOOL] phase cards
argument-hint: <sprint goal>
---

# /sprint-plan

Plan a sprint/iteration around the governing **goal** in `$ARGUMENTS`, following
[.claude/workflows/sprint-management.md](../workflows/sprint-management.md) and producing a
[sprint-plan document](../templates/sprint-plan.md).

## Execution flow
1. **State the goal.** Restate the single statement of what this sprint must deliver. Everything below is measured against it.
2. **Decompose into phases.** Break delivery into implementation phases. For each phase: the outcome it produces and the evidence that proves it.
3. **Doctrine fit.** Confirm the plan aligns with [PROJECT_DOCTRINE] (see [domain-knowledge](../context/domain-knowledge.md)). Flag anything that drifts from the stated goal.
4. **[PM_TOOL].** Per [trello rules](../rules/trello.md): one `[CARD_PREFIX]...` card per phase in [BACKLOG_LIST], with non-technical, outcome-oriented checklist items and reused labels. Check for existing cards first — never duplicate.
5. **Risks & open decisions.** List anything needing a product call before building.

## Expected output
- A filled [sprint-plan template](../templates/sprint-plan.md): goal, phases, doctrine fit, risks.
- [PM_TOOL] [BACKLOG_LIST] cards created/updated for each phase.
- Phases framed by outcome, aligned with [PROJECT_DOCTRINE].
