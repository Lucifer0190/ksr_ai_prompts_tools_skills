# Workflow — Sprint Management & [PM_TOOL] Synchronization

> The canonical procedure for mirroring development into [PM_TOOL]. Referenced by every other
> workflow and by `/sprint-plan`. Standing policy: [trello rules](../rules/trello.md);
> connection safety: [mcp rules](../rules/mcp.md); wording: [pm-conversion](../prompts/pm-conversion.md).

## Preflight (every time)
1. Verify [PM_TOOL] MCP is connected and authorized; verify board **[BOARD_NAME]** is reachable.
2. If not, notify the user and stop.
3. `get_lists` to confirm the **[BACKLOG_LIST] → [IN_PROGRESS_LIST] → [REVIEW_LIST]** lists; `get_board_labels` to know which Type/Area/Priority labels exist (reuse only).

## Card lifecycle state machine
```
(plan)        → create card in [BACKLOG_LIST]        [one per implementation phase]
(start work)  → move [BACKLOG_LIST] → [IN_PROGRESS_LIST]
(progress)    → tick checklist items + add progress comment   [continuously]
(scope grows) → add checklist items            [never silently expand]
(phase done)  → move [IN_PROGRESS_LIST] → [REVIEW_LIST]       [STOP — never beyond [REVIEW_LIST], never archive]
```

## Creating a card (only after checking for duplicates)
1. `search` / `get_cards` for an existing `[CARD_PREFIX]<phase>` card. If found → update it, do not duplicate.
2. `create_card` in [BACKLOG_LIST] with a non-technical title prefixed `[CARD_PREFIX]`.
3. `add_label_to_card` using the most relevant existing Type/Area/Priority labels.
4. `create_checklist` + `add_checkitem` with outcome-oriented items, including validation/QA/rollout items.

## During development
- `update_checkitem` to tick items as work lands — keep near-real-time.
- `add_comment` after each major milestone, in PM-friendly language (impact, not implementation).
- Discovered work → `add_checkitem` immediately.

## On completion
- All checklist items ticked, final progress comment added, `update_card` to move to **[REVIEW_LIST]**.

## Sprint-level (for `/sprint-plan`)
- State the governing **goal**; frame phases by the outcome each delivers, aligned with [PROJECT_DOCTRINE].
- One card per phase; track the sprint's health by its progress against the goal, per [PROJECT_DOCTRINE].
