# Context — Architecture Overview

> The map of the system (what lives where). The *rules* for building within it are in
> [rules/architecture.md](../rules/architecture.md) and [rules/backend.md](../rules/backend.md).
> Full engineering plan: `[DOCS_DIR]/technical-spec`.
>
> Fill in each section for [PROJECT_NAME]. Keep diagrams as fenced blocks. Delete tiers/surfaces
> that don't apply.

## Identity & access
> Sketch how identities map to roles/tenants, then state the resolution rule.
```
[auth/identity source — one row per human]
 ├── [top-tier membership]   → [ADMIN_ROLE]   ([scope])
 └── [mid-tier membership]   → [MANAGER_ROLE] ([scope])
        └── [leaf membership] → [EDITOR_ROLE] | [VIEWER_ROLE] ([per-resource scope])
```
Effective role resolves **highest-tier-wins** in a single helper ([SRC_DIR]/.../resolveRole):
[ADMIN_ROLE] → [MANAGER_ROLE] of owning scope → leaf role → else **404** (never reveal existence).

## Route / module surfaces
> The top-level surfaces of the app and who can reach each. Use your framework's routing idiom.
```
[/admin-or-top-tier surface]      [ADMIN_ROLE] only — gated by [the top-tier membership check]
[/mid-tier surface]               [MANAGER_ROLE] — [what they manage]
[/leaf/[id] surfaces]             per-resource surfaces by role:
    [role-specific sub-surfaces]
[other existing surfaces]         [list the main user-facing routes/screens]
```
Gating: [where access is enforced — e.g. middleware + per-page server check]. Auth surfaces: [login / forgot-password / invite routes].

## Code layout
> The source tree the assistant will navigate most. Adjust to your language/framework conventions.
```
[SRC_DIR]/
  [routes/]     route or page tree
  [api/]        server endpoints (grouped by tier/feature)
  lib/
    auth/       role resolution + access guards
    ai/         AI logic (if any) — prompts referenced from [DOCS_DIR]/ai-prompts
    [BACKEND_PLATFORM]/   data clients (server + browser) + generated types
    hooks/      shared hooks/utilities
  components/   ui/, layout/, feature-scoped folders
[DOCS_DIR]/     [SCHEMA_FILE] (source of truth), product-overview, technical-spec,
                design-system, ai-prompts, user-flows
```

## Session shape
> What the "who am I / what can I see" endpoint or session object returns, and how it's cached.
[Describe the session payload — e.g. `{ user, <top-tier flag>, <tenants:[…roles, scopes]> }` —
where it's cached, and when it's re-fetched (e.g. on tenant/scope switch).]

## Data flow invariants
> The cross-cutting rules that must always hold.
- Tenancy is enforced at the data layer (row-level security / equivalent); UI gating is convenience only.
- Every mutation writes an audit record; every AI call (if any) writes an AI call log.
- Schema changes go in [SCHEMA_FILE] (idempotent, re-runnable) — no ad-hoc migration files.
