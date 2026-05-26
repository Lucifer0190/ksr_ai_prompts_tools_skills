# Prompt — Technical → PM Conversion

> Reusable system for turning engineering work into stakeholder-friendly [PM_TOOL] wording.
> Used whenever creating/updating [PM_TOOL] cards ([trello rules](../rules/trello.md),
> [sprint-management](../workflows/sprint-management.md)).

## Goal
Rewrite technical implementation work as clear, non-technical, outcome-oriented language a
non-engineer stakeholder understands.

## Rules
- Lead with **purpose, impact, capability, improvement, operational value, or business outcome**.
- **Avoid** filenames, APIs, schemas, routes, language internals, migrations, DB internals, frameworks,
  and low-level engineering terms — unless absolutely necessary for clarity.
- Card titles: prefix `[CARD_PREFIX]`, describe the capability, not the code.
- Checklist items: short, actionable, outcome-oriented; include validation/QA/rollout items.

## Conversion patterns
> Examples — adapt to your own domain vocabulary.
| Technical | PM-friendly |
|---|---|
| "Add access-control policy traversing tenant→scope on the main resource table" | "Ensure people only see work inside their own organisation" |
| "Implement the highest-tier role resolver" | "Make sure each person gets the right level of access automatically" |
| "Wire the gating endpoint, score < threshold → flagged for review" | "Have the system flag weak items for a human to decide on" |
| "Regenerate generated types after a schema change" | "Keep the system's data definitions in sync" |
| "Add loading + error + empty states to a screen" | "Make every screen handle loading, errors, and no-data gracefully" |

## Output
For any work item, produce: a `[CARD_PREFIX]...` title + 3–6 outcome-oriented checklist items
(including a validation/QA item) + a one-line progress comment for when it ships.
