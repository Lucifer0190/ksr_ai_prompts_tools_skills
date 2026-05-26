# Template — Bug Report

> Use to capture a defect before fixing. Drives the [bug-resolution workflow](../workflows/bug-resolution.md).

```markdown
## Title
<short, user-impact-oriented>

## Environment
- Role: <[ADMIN_ROLE] | [MANAGER_ROLE] | [EDITOR_ROLE] | [VIEWER_ROLE]>
- Surface/route: <e.g. /[feature]/[id]>
- Browser/device + viewport: <e.g. mobile 375px>

## Steps to reproduce
1.
2.
3.

## Expected vs actual
- Expected: <...>
- Actual: <...>

## Evidence
<console errors, screenshot path, failing request, AI-call-log/audit-log entry>

## Severity / impact
<blocker | major | minor> — <who is affected and how>

## Root cause (filled during diagnosis)
<symptom → cause; the actual defect, not the surface>

## Fix & regression test
- Fix: <smallest correct change>
- Test: <name of the regression test that now guards it>
```
