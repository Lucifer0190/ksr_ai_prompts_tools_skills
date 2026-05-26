---
description: Diagnose and fix a bug following the [PROJECT_NAME] bug-resolution workflow
argument-hint: <bug description or issue link>
---

# /bugfix

Resolve the bug in `$ARGUMENTS` by executing
[.claude/workflows/bug-resolution.md](../workflows/bug-resolution.md).

## Execution flow
1. **Reproduce.** Establish the exact failing behavior; capture it in a [bug report](../templates/bug-report.md). If you can't reproduce, say so and ask for steps.
2. **Diagnose.** Use [deep-debugging](../prompts/deep-debugging.md) — find root cause, not the symptom. State the cause before editing.
3. **[PM_TOOL].** Find/create the card, move to [IN_PROGRESS_LIST], note the defect in the checklist (non-technical).
4. **Fix.** Smallest correct change. Respect all rules. Add a regression test that fails before and passes after.
5. **Verify.** [QA checklist](../checklists/qa.md): [TYPECHECK_CMD], [LINT_CMD], build, reproduce-then-confirm-fixed.
6. **Sync & finish.** Tick checklist, progress comment, move card to [REVIEW_LIST]. Log root cause in [memory/known-issues.md](../memory/known-issues.md) if it reveals a pattern.

## Expected output
- Root-cause statement.
- Minimal fix + regression test.
- Updated [PM_TOOL] card + memory note.
- Verification proving the bug is gone.
