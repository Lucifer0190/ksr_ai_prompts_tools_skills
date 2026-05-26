# Rule — Performance

> Cheap-to-hold constraints that keep [PROJECT_NAME] fast as data and tenants grow.

## Rendering
- Server-render by default; ship the smallest possible client bundle. Push client-only code to leaf components, not page roots.
- Stream with suspense + a route loading state so first paint isn't blocked on data.
- Never fetch in a client component (also an [architecture](architecture.md) rule) — it causes client waterfalls.

## Data
- Fetch only the columns/rows needed; let row-level security + explicit field selection narrow results. Paginate server-side for large lists (client-table pagination is UI-only).
- Avoid N+1 round-trips to the [BACKEND_PLATFORM]; batch related reads.
- Cache the current-session/`me` lookup in the layout context provider; re-fetch only on tenant/workspace switch.

## Assets & layout
- Prevent layout shift: skeletons and charts reserve their final height.
- Use the framework's optimized image component for raster images; lazy-load below-the-fold media.
- Memoize expensive client derivations and stable callbacks only where a real re-render cost exists — don't cargo-cult.

## AI calls
- AI calls are typically the slowest path: show optimistic/pending UI, log to the AI call log, and never block unrelated UI on them.
