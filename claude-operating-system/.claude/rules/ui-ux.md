# Rule — UI / UX

> Layout, state coverage, and product look-and-feel. Library mechanics are in
> [frontend.md](frontend.md); verification is in [.claude/checklists/qa.md](../checklists/qa.md).

## Responsive — mobile first
Write base styles for mobile, scale up with responsive modifiers (e.g. `sm:`/`md:`/`lg:`). Never write desktop-only styles without a mobile base.
```tsx
// ✅ <div className="flex flex-col gap-4 p-4 md:flex-row md:gap-6 md:p-6">
// ❌ <div className="flex flex-row gap-6 p-6">
```
Breakpoints (common defaults — adjust to your design system):
- `<768px (md)` — single column, bottom-drawer modals, hidden secondary table columns.
- `768–1024px` — sidebar collapsed to icons, two-column content.
- `>1024px (lg)` — full sidebar, three-column grids allowed.

Sidebar: mobile = off-canvas hamburger overlay; tablet = ~64px icon-only with tooltip labels; desktop = ~240px, animated collapse.

Touch targets: minimum **44×44px** on interactive elements (`min-h-[44px] min-w-[44px]`).

## Required UI states (every data view)
- **Loading** — skeleton matching the real layout (same columns, heights). Never a lone spinner.
- **Error** — an error boundary with a retry button and support message.
- **Empty** — icon + headline + subtext + a CTA. Never render an empty container.
```tsx
{items.length === 0 ? <EmptyState .../> : <DataView items={items} />}
```

## [PROJECT_NAME] product look (doctrine-locked — see [DESIGN_SYSTEM_REF])
- [Describe your design system: tone, light/dark mode, background, accent usage. Replace this with the locked look-and-feel from [DESIGN_SYSTEM_REF].]
- [Layout defaults: content max-width, column count, shadow/chrome density.]
- [Any view-specific rules — e.g. which dashboards may or may not show charts/lists, per [PROJECT_DOCTRINE].]
- [Information priority: what the primary view leads with vs. relegates.]
