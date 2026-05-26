# Checklist — Accessibility Audit

> Executable a11y gate. Pairs with [rules/accessibility.md](../rules/accessibility.md).
> Run on every component touched; fix all accessibility-lint errors (e.g. `jsx-a11y`) — don't suppress.

## Focus
- [ ] Every interactive element has a visible focus ring (`focus-visible:ring-2 ...`)
- [ ] No `outline: none` without a replacement ring
- [ ] Modal/drawer: focus moves inside on open, returns to trigger on close

## Semantics
- [ ] Real elements used: `<button>`, `<nav aria-label>`, `<main>`, `<table><thead><tbody>`
- [ ] No `<div onClick>` standing in for a button/link

## ARIA & labels
- [ ] Every icon-only button has `aria-label`
- [ ] Every `<input>` has a `<label htmlFor>` matching its `id`
- [ ] Errored inputs: `aria-invalid` + `aria-describedby`; messages have `role="alert"`
- [ ] Dynamic status: `role="status"`; loading containers: `aria-busy="true"`

## Color & contrast
- [ ] Normal text ≥ 4.5:1; large text ≥ 3:1 (WCAG AA)
- [ ] No information conveyed by color alone (paired with icon/text)

## Keyboard
- [ ] Entire feature operable without a mouse
- [ ] Table row actions reachable by keyboard
- [ ] Menus: arrows navigate, Escape closes, Tab exits

## Tooling
- [ ] `[LINT_CMD]` shows zero accessibility-lint (e.g. `jsx-a11y`) violations
