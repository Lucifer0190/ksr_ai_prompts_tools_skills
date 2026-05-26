# Checklist — QA (run before marking any task done)

> The general self-audit gate. Derived from the original CLAUDE.md self-audit checklist.
> Claude: execute each item; report pass/fail honestly; fix failures before claiming done.

## Automated
- [ ] `[TYPECHECK_CMD]` — zero type errors
- [ ] `[LINT_CMD]` — zero errors (including accessibility lint)
- [ ] `[BUILD_CMD]` — succeeds (for non-trivial changes)

## Route completeness
- [ ] Loading state exists and uses a skeleton matching the page layout (not a spinner)
- [ ] Error boundary exists with a retry button + support message
- [ ] Empty state handled: icon + message + CTA (no bare empty container)

## Components & libraries
- [ ] All [STYLING] classes composed via the shared class utility — no template-literal class joins
- [ ] No hardcoded brand color values — design-token references only
- [ ] Modals: desktop dialog / mobile bottom drawer (<768px) via the chosen libraries
- [ ] Async actions use a promise-aware toast — not manual `.then()` toasts
- [ ] Dynamic lists/table bodies use the auto-animation helper
- [ ] Forms use the chosen form + schema-validation libraries, with inline field errors (not toast-only)
- [ ] Animations respect `prefers-reduced-motion`

## Responsive & interaction
- [ ] No horizontal overflow at 375px; text doesn't overflow
- [ ] Touch targets ≥ 44×44px on interactive elements
- [ ] Server-rendered by default; client boundaries only where required

## Behavioral
- [ ] Change verified in the running app (not just by reading code) — note what was observed
- [ ] Doctrine-critical paths have test coverage (see [testing rule](../rules/testing.md))

## Sync
- [ ] [PM_TOOL] card updated (checklist ticked, progress comment, moved to correct list)
- [ ] New decisions/debt/avoided-patterns recorded in [memory/](../memory/)
