# Rule — Testing & Verification

> What "verified" means before claiming done. The QA gate is
> [.claude/checklists/qa.md](../checklists/qa.md).

## Standing gates (run before marking work complete)
- **Type check**: `[TYPECHECK_CMD]` — zero errors.
- **Lint**: `[LINT_CMD]` — zero errors, including accessibility lint. Fix a11y errors, don't suppress them.
- **Build** (for non-trivial changes): `[BUILD_CMD]` must pass.

## Manual / behavioral verification
- Confirm a change in the actual running app, not just by reading code (use the `verify` / `run` skills). Report what you observed.
- Smoke-test critical surfaces (e.g. auth/login) — if the repo has a screenshot/visual path, use it to confirm they render.

## E2E ([TEST_FRAMEWORK])
- `[TEST_FRAMEWORK]` is the e2e tool. Cover the critical [PROJECT_DOCTRINE] paths end to end (the core lifecycle and any gating thresholds defined in [domain-knowledge.md](../context/domain-knowledge.md)).
- Cover role isolation: a contributor cannot read another contributor's private data; a [VIEWER_ROLE] cannot mutate; cross-tenant access 404s.

## Honesty
- If tests fail, say so with the output. If a step was skipped, say which. Never report "done" for unverified work.
