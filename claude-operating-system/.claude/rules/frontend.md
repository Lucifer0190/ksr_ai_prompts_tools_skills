# Rule — Frontend Libraries

> Mandatory usage patterns for the project's load-bearing UI libraries. These are constraints,
> not tutorials: use the chosen library for each concern, or surface why you can't. Install list
> and versions: [.claude/context/stack.md](../context/stack.md).
>
> List your actual libraries in `stack.md`, then make each principle below point at them. The
> `Example (React stack): …` snippets show one concrete implementation — replace with yours.

## Accessible primitives — `[your accessible-primitive library]`
Use a dedicated accessible-primitive library for: Dialog, DropdownMenu, Tooltip, Popover, Select, Checkbox, RadioGroup, Switch, Tabs, AlertDialog, HoverCard, ContextMenu. Never rebuild these from `<div>` + click handlers — the library handles keyboard nav, focus trapping, ARIA, and screen-reader announcements.

```tsx
// Example (React stack — Radix):
import * as Dialog from '@radix-ui/react-dialog'
<Dialog.Root>
  <Dialog.Trigger asChild>{trigger}</Dialog.Trigger>
  <Dialog.Portal>
    <Dialog.Overlay className="fixed inset-0 bg-black/50" />
    <Dialog.Content className="fixed left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 w-full max-w-lg rounded-xl bg-white p-6 focus:outline-none">
      {children}
    </Dialog.Content>
  </Dialog.Portal>
</Dialog.Root>
```
Rules: never nest interactive elements inside triggers; always give dialogs an accessible title (visually hidden is fine) and a description / `aria-describedby`; on small screens (`<768px`) prefer a bottom drawer over a centered modal (see below).

## Forms — `[your form library]` + `[your schema/validation library]` (no exceptions)
Every form uses the chosen form library plus a schema validator.
```tsx
// Example (React stack — react-hook-form + zod):
const schema = z.object({ email: z.string().email('Invalid email address') })
type FormData = z.infer<typeof schema>
const { register, handleSubmit, formState: { errors, isSubmitting } } =
  useForm<FormData>({ resolver: zodResolver(schema) })
```
Rules:
- Disable native browser validation; the schema validates, not the browser.
- `aria-invalid` on errored inputs; `aria-describedby` → the error element id.
- `role="alert"` on each error message so screen readers announce it.
- Loading/disabled state on the submit control while submitting.
- **Always show inline field errors** — never errors-as-toast-only (a toast may *also* fire, see toasts).

## Data tables — `[your data-table library]`
All non-trivial tables use the chosen table library — never raw markup + manual sort state. Wire core + sorted + filtered + paginated data with controlled state. On small viewports, hide secondary columns, offer a card view for wide tables (5+ columns), and provide a column-visibility toggle. Pagination must be keyboard navigable.

## Mobile drawers — `[your drawer library]`
Below `768px`, replace centered modals with a bottom drawer. Build one responsive wrapper that renders a desktop dialog and a mobile drawer based on a viewport media query.

## Animations — `[your animation library]`
Use shared animation presets only (e.g. `fadeIn`, `slideUp`, `slideInRight`) — never ad-hoc durations.
- Page transitions: wrap route children in a fade preset.
- Modals/drawers: wrap in an exit-animation-aware container so close animations play.
- Lists: animate list items with a stagger.
- Sidebar collapse: animate width between collapsed/expanded.
- **Always respect `prefers-reduced-motion`** (zero duration when reduced).

## List/auto-animation
Add lightweight auto-animation to dynamic lists: table bodies, sidebar nav lists, notification/alert lists, and card/kanban lists.

## Toasts — `[your toast library]`
Mount a single toaster in the root layout. Never use `alert()` / `window.confirm()` / inline-only success.
- Async actions use a promise-aware toast — never a manual success toast after a `.then()`.
- Form failures: toast **and** inline error.
- Destructive actions: a confirm dialog first — a toast is never the only confirmation.

## Charts — `[your charts library]`
Always make charts responsive to their container width; always render a same-height loading skeleton to prevent layout shift.
> ⚠️ **Doctrine tension:** [PROJECT_NAME] may restrict where charts are allowed (see [PROJECT_DOCTRINE]). A charts library may be installed and used in some areas (e.g. health/admin), but **respect the views where doctrine forbids charts.** See [.claude/memory/decisions.md](../memory/decisions.md).

## Icons
Use a single icon library. Icon-only controls require `aria-label` (see [accessibility.md](accessibility.md)).

## Realtime / drag-and-drop
Realtime presence/multiplayer, drag-and-drop, and connector-drawing libraries are client-only — isolate them in client leaf components and keep data fetching in the server parent.
