# Context — Glossary

> Canonical vocabulary for [PROJECT_NAME]. Use these exact terms in code, UI, and [PM_TOOL].
> Fill in the roles and domain terms your project actually uses; delete tiers you don't have.

## Roles
> List every role, its system identifier (the value stored in code/DB), and a one-line scope.
> Order them highest-privilege first. Keep identifiers stable — they appear in [rules/naming.md](../rules/naming.md).
- **[ADMIN_ROLE]** — [describe scope: what this top-tier role can see/do across the whole system].
- **[MANAGER_ROLE]** — [describe scope: mid-tier / team-lead reach and limits].
- **[EDITOR_ROLE]** — [describe scope: standard contributor — what they create/edit and what they can't].
- **[VIEWER_ROLE]** — [describe scope: read-only — what they can see; confirm they can never mutate].

## Domain terms
> The handful of words that mean something specific in your product. Define each precisely so
> code, UI copy, and PM cards all use the term the same way. Add/remove as needed.
- **[DOMAIN_TERM_1]** — [precise definition; note the table/field or flow it maps to, if any].
- **[DOMAIN_TERM_2]** — [precise definition].
- **[DOMAIN_TERM_3]** — [precise definition].

## Hierarchy
> Sketch how identities and tenancy nest, if your product is multi-tenant or layered.
```
[auth/identity] → [top-tier grouping] → [mid-tier grouping] → [leaf scope / per-resource role]
```

## Key entities / tables
> The core data objects (DB tables, collections, or models) the assistant will touch most.
`[entity_1]`, `[entity_2]`, `[entity_3]`, `[audit/log entity]`, `[ai/call-log entity (if any)]`.
