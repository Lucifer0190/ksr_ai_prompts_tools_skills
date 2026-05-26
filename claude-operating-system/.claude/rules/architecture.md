# Rule — Architecture ([FRAMEWORK])

> How code is structured and where it lives. Pairs with
> [.claude/context/architecture-overview.md](../context/architecture-overview.md) (the *map* of the system).

## Server vs Client boundaries
- Default to **server-rendered** units. Opt into client-side rendering only when required.
- Move to a client component/boundary only for: local state, lifecycle effects, event handlers, browser-only APIs, and client-only libraries (animation, accessible-primitive, form, table, realtime, drag-and-drop libs).
- **Never fetch data inside a client component.** Fetch in the server parent, pass as props.
- Wrap async server units in a suspense boundary + a route-level loading state.

## Required files per route
Every route directory must contain its framework's equivalents of:
```
[route]/
  page            ← server unit: fetches data, passes to client children
  loading         ← skeleton UI matching the page layout — never a bare spinner
  error           ← client error boundary with a retry button + support message
```
Skeleton and empty/error-state requirements are specified in [ui-ux.md](ui-ux.md).

## Component file structure
```
components/
  ui/         ← reusable primitives (Button, Input, Badge, Modal)
  layout/     ← AppShell, Sidebar, TopBar, PageHeader
  features/   ← feature-scoped folders, one per domain area
  charts/     ← chart wrappers (see ui-ux.md note on the charts-vs-doctrine tension)
```

## Role & access resolution
- Resolve the effective role once per request via a single helper ([SRC_DIR]/.../resolveRole) — highest tier wins ([ADMIN_ROLE] → [MANAGER_ROLE] → scoped role → 404). Every API route and page calls it once and trusts the result. See [security.md](security.md).

## Boundaries
- API routes resolve tenant/org context from the scope they target.
- Keep AI logic in one place (e.g. [SRC_DIR]/.../ai); keep [BACKEND_PLATFORM] clients in one place (e.g. [SRC_DIR]/.../[BACKEND_PLATFORM]). Don't inline either into components.
