# Rule — Accessibility (non-negotiable)

> These must pass in every component. Fix accessibility-lint errors (e.g. `jsx-a11y`) before moving on.
> The executable audit is [.claude/checklists/accessibility.md](../checklists/accessibility.md).

## Focus
- Every interactive element has a visible focus ring: `focus-visible:ring-2 focus-visible:ring-blue-500 focus-visible:outline-none`.
- Never `outline: none` without a replacement ring.
- On modal/drawer open, focus moves to the first interactive element; on close it returns to the trigger (a good accessible-primitive library does this automatically — don't fight it).

## Semantic HTML
- Use `<nav aria-label>`, `<main>`, `<button type="button|submit">`, `<table><thead><tbody>`.
- Never `<div onClick>`. Only use `role="button"` if a real `<button>` is truly impossible.

## ARIA
- Icon-only buttons: always `aria-label`.
- `<input>`: always a `<label htmlFor>` matching `id`.
- Dynamic status text: `<span role="status">`; loading containers: `aria-busy="true"`.
- Form errors: `aria-invalid` on input, `aria-describedby` → error id, `role="alert"` on the message.

## Color & contrast
- Normal text ≥ 4.5:1; large text (18px+, or 14px bold) ≥ 3:1 (WCAG AA).
- Never convey meaning by color alone — pair with icon or text.

## Keyboard
- Every feature usable without a mouse. Table row actions (edit/delete) reachable by keyboard.
- Menus: arrow keys navigate, Escape closes, Tab moves on.
