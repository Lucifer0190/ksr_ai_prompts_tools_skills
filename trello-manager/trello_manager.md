# Rule — Trello Project Management

> Standing policy for keeping Trello synchronized with development. Drop this file into your
> project's `.claude/rules/` folder and reference it from `CLAUDE.md`.
>
> **📌 Setup:** replace the `[SQUARE_BRACKET]` placeholders below with your own board name,
> card prefix, and list names before using.

You are responsible for keeping Trello updated alongside development work.

## Preflight (always, before any Trello action)
- Verify the Trello MCP server is connected and authorized.
- Verify access to the board is available.
- If MCP is unavailable/unauthorized, **notify the user before continuing** — do not attempt Trello operations on a failed connection.

**Board:** [BOARD_NAME]

## Card naming
- Prefix every card title with `[CARD_PREFIX]`.
  - e.g. `[CARD_PREFIX]Improve Onboarding Flow`, `[CARD_PREFIX]Build Reporting Dashboard`.
- Convert technical work into clear, non-technical titles and checklist items understandable by stakeholders.
- Focus on purpose, impact, capability, improvement, operational value, or business outcome.
- Avoid filenames, APIs, schemas, routes, languages, migrations, DB internals, frameworks, or low-level engineering terms unless absolutely necessary for clarity.

## Labels
- Always reuse existing labels (Type / Area / Priority). Apply the most relevant available ones.
- **Do not create new labels** unless explicitly instructed.

## Card lifecycle (never skip, never duplicate)
- One card per implementation **phase**.
- Before creating: check whether a related card already exists; **update it instead of duplicating**.
- New phase cards go to **[BACKLOG_LIST]**.
- When development starts → move to **[IN_PROGRESS_LIST]**.
- When the phase is complete → move to **[REVIEW_LIST]**. **Never move beyond [REVIEW_LIST]. Never archive.**

## Checklists & comments
- Checklist items: concise, actionable, non-technical, outcome-oriented (not implementation-oriented).
- Include validation/QA/testing/rollout/verification items whenever applicable.
- Update checklist items continuously as work progresses; tick items as they complete.
- Add a short, non-technical progress comment after each major milestone.
- If new implementation work is discovered, automatically add checklist items for it.

## Synchronization principle
Maintain Trello as a continuously updated, near-real-time implementation tracker. Keep cards, labels, statuses, and checklist completion aligned with actual implementation state and discovered scope changes.
