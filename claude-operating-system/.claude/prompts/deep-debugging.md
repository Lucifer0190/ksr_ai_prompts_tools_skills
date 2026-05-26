# Prompt — Deep Debugging

> Reusable root-cause procedure. Drives the [bug-resolution workflow](../workflows/bug-resolution.md).
> Goal: fix the cause, never the symptom.

## Procedure
1. **Reproduce deterministically.** Exact steps, role, route, viewport. If you can't reproduce, stop and gather data — don't guess-patch.
2. **Observe, don't assume.** Read the actual error, stack, failing request/response, and relevant audit-log / AI-call-log rows. Reproduce in the running app.
3. **Form one hypothesis at a time.** State "I believe X causes Y because Z." Make the smallest change or add the cheapest probe that would confirm or refute it.
4. **Bisect.** Narrow the failure: which layer (access control? role resolver? client/server boundary? realtime race? a core domain gate?), which commit, which input.
5. **Confirm the cause.** Don't fix until you can explain the mechanism. Distinguish symptom from cause explicitly.
6. **Fix at the root + guard it.** Smallest correct change; add a regression test that fails before and passes after.
7. **Check for siblings.** Does the same root cause exist elsewhere? Fix or log them.

## [PROJECT_NAME]-specific suspects
> Replace with the recurring failure points in your codebase. Examples:
- Access bugs → the role resolver / access-control traversal (often surfaces as a wrong 404 or a leak).
- A domain gate misfiring → the threshold / decision path that gate depends on.
- Realtime desync → client realtime state vs. server state.
- Hydration / client-boundary errors → data fetched inside a client component.

## Output
Root-cause statement, the fix, the regression test, and — if it's a recurring trap —
an entry in [memory/known-issues.md](../memory/known-issues.md) or [avoided-patterns.md](../memory/avoided-patterns.md).
