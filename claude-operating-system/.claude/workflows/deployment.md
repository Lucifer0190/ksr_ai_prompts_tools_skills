# Workflow — Deployment ([HOSTING])

> Procedure for deploying [PROJECT_NAME]. Invoked as part of `/release`. Deployment is
> outward-facing — confirm with the user before triggering.

## 1. Pre-deploy gate
- Run the [deployment checklist](../checklists/deployment.md) and [pre-release checklist](../checklists/pre-release.md). Stop on any blocker.
- Confirm the branch is merged/intended and builds clean ([BUILD_CMD]).

## 2. Database
- If [SCHEMA_FILE] changed, confirm it has been applied to the target [BACKEND_PLATFORM] project (it is idempotent and re-runnable). Access-control policies rebuild on re-run.
- Confirm generated types ([SRC_DIR]/.../types) were regenerated to match.

## 3. Environment
- Verify required env vars exist in the [HOSTING] target environment ([BACKEND_PLATFORM] URL/keys, [AI_PROVIDER] key). Server-only keys must not use the client-public prefix.
- Cross-check against the env example file.

## 4. Deploy
- Trigger the [HOSTING] deploy for the intended environment (preview vs production). Confirm production intent with the user.

## 5. Post-deploy verification
- Smoke the critical surfaces: auth/login, an admin entry point, a primary dashboard, and the core [PROJECT_DOCTRINE] lifecycle path.
- Confirm the audit log and AI call log are recording. Check the health/observability view.

## 6. Track
- Move included [PM_TOOL] cards to **[REVIEW_LIST]**; add a deploy comment. Update [memory/roadmap.md](../memory/roadmap.md).
- On failure: roll back the [HOSTING] deployment, log the cause in [memory/known-issues.md](../memory/known-issues.md), and notify the user.
