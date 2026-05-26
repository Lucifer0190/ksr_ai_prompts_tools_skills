# Rule — Naming

> Keep names predictable so the codebase stays navigable as it grows.
> Adjust the casing conventions below to your [LANGUAGE]'s idioms.

## Files & folders
- Components / view units: match your framework's convention (e.g. `PascalCase` files like `SprintTaskCard`).
- Hooks / composables: prefix per convention (e.g. `useThing`).
- Utilities / libs: consistent casing (e.g. `camelCase` like `resolveRole`, `cn`).
- Route folders: lowercase, kebab where multi-word; use your framework's grouping convention.
- One primary export per file; the filename matches the export.

## Symbols
- Types & view units: `PascalCase`. Functions, variables, props: `camelCase`. Constants/enum values: `UPPER_SNAKE` only for true constants.
- Booleans read as predicates: `isActive`, `hasFlag`, `canEdit`.
- Event handlers: `handleX` for definitions, `onX` for props.
- Validation schemas: `xSchema`; inferred type alongside it.

## Domain vocabulary (use these exact terms — see [glossary](../context/glossary.md))
- Roles: `[ADMIN_ROLE]`, `[MANAGER_ROLE]`, `[EDITOR_ROLE]`, `[VIEWER_ROLE]`. If a legacy value is being migrated to a new name, use the new name in new code and retain the old one only as a transitional value.
- Domain terms: use the exact terms defined in the [glossary](../context/glossary.md) (e.g. `[DOMAIN_TERM_1]`, `[DOMAIN_TERM_2]`, `[DOMAIN_TERM_3]`).

## [PM_TOOL] (PM-facing names)
- Card titles are non-technical and prefixed `[CARD_PREFIX]` — see [trello.md](trello.md).
