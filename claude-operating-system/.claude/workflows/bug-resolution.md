# Workflow — Bug Resolution

> Autonomous procedure for fixing a defect. Invoked by `/bugfix`.

## 1. Reproduce
- Establish exact failing behavior, environment, and steps. Capture in a [bug report](../templates/bug-report.md).
- If you cannot reproduce, stop and request steps — never guess-fix.

## 2. Diagnose root cause
- Apply [deep-debugging](../prompts/deep-debugging.md): trace from symptom to cause; form a hypothesis; confirm it with evidence (logs, a failing test, narrowed repro).
- State the root cause explicitly **before** editing. Distinguish symptom from cause.

## 3. Track (transition: → [IN_PROGRESS_LIST])
- Find/create the [PM_TOOL] card, move to **[IN_PROGRESS_LIST]**, add a non-technical note of the defect's user impact.

## 4. Fix
- Smallest correct change at the root cause. Respect all [rules](../rules/).
- Add a **regression test** that fails on the old code and passes on the new.

## 5. Verify
- [QA checklist](../checklists/qa.md): [TYPECHECK_CMD], [LINT_CMD], build.
- Re-run the original repro and confirm it's resolved; confirm no collateral regressions.

## 6. Close (transition: → [REVIEW_LIST])
- Tick checklist, progress comment, move card to **[REVIEW_LIST]**.
- If the bug reveals a recurring trap, log it in [memory/known-issues.md](../memory/known-issues.md) and/or [avoided-patterns.md](../memory/avoided-patterns.md).

## Update behavior
If the root cause is broader than the reported symptom, surface the larger problem and propose scope before expanding the fix.
