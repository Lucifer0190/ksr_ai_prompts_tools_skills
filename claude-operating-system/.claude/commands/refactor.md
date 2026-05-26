---
description: Refactor code safely with no behavior change
argument-hint: <target file/module/area>
---

# /refactor

Refactor `$ARGUMENTS` to improve clarity, reduce duplication, and separate responsibilities
— **with zero behavior change.**

## Execution flow
1. **Baseline.** Read the target and its callers. Confirm test/behavioral coverage exists; if not, add characterization tests first so you can prove behavior is unchanged.
2. **Check memory.** Read [avoided-patterns](../memory/avoided-patterns.md) and [tech-debt](../memory/tech-debt.md) — refactor toward the documented direction, not against it.
3. **Plan.** State the smell, the target shape, and the steps. For large refactors, write an [implementation plan](../templates/implementation-plan.md).
4. **Refactor incrementally.** Each step compiles and passes tests. Respect [coding](../rules/coding.md), [architecture](../rules/architecture.md), [naming](../rules/naming.md).
5. **Verify equivalence.** [TYPECHECK_CMD], [LINT_CMD], build, and the full test suite green. Diff behavior, not just code.
6. **Record.** Update [tech-debt.md](../memory/tech-debt.md) (debt paid down) and [PM_TOOL] if this was a tracked phase.

## Constraints
- No feature changes, no API signature changes unless explicitly requested.
- If you discover a bug mid-refactor, stop and surface it — don't silently fix behavior inside a refactor.

## Expected output
- Cleaner code, identical behavior, passing checks, updated debt ledger.
