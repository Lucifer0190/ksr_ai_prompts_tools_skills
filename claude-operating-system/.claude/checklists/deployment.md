# Checklist — Deployment ([HOSTING])

> Run during the [deployment workflow](../workflows/deployment.md). Confirm production intent
> with the user before triggering a production deploy.

## Pre-deploy
- [ ] Target branch merged/intended; `[BUILD_CMD]` clean
- [ ] [QA](qa.md), [accessibility](accessibility.md), [security-review](security-review.md) all pass
- [ ] No debug code, console spam, or temporary instrumentation left in

## Database
- [ ] If `[SCHEMA_FILE]` changed, it has been applied to the target [BACKEND_PLATFORM] project (idempotent re-run)
- [ ] Generated types ([SRC_DIR]/.../types) regenerated to match
- [ ] Access/row-level-security policies verified after schema re-run

## Environment
- [ ] All required env vars present in the [HOSTING] target ([BACKEND_PLATFORM] URL + keys, [AI_PROVIDER] key)
- [ ] Server-only keys are NOT exposed with the public client prefix
- [ ] Cross-checked against the example env file

## Deploy & verify
- [ ] Correct environment chosen (preview vs production) — production confirmed with user
- [ ] Post-deploy smoke: auth/login, primary dashboard, and the core [PROJECT_DOCTRINE] path
- [ ] Audit log + AI call log recording; health/observability view green

## Track
- [ ] Included [PM_TOOL] cards moved to **[REVIEW_LIST]** (never beyond) with a deploy comment
- [ ] [memory/roadmap.md](../memory/roadmap.md) updated
- [ ] Rollback plan known; on failure, roll back and log in [memory/known-issues.md](../memory/known-issues.md)
