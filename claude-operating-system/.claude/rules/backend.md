# Rule — Backend ([BACKEND_PLATFORM], API, AI)

> Server-side constraints. Schema/auth detail lives in [DOCS_DIR]/technical-spec and
> [SCHEMA_FILE] (the idempotent source of truth — **no migration files**).

## Database / [BACKEND_PLATFORM]
- Schema changes go into [SCHEMA_FILE] only. It is idempotent and re-runnable; never create ad-hoc migration files.
- Regenerate generated types ([SRC_DIR]/.../types) after any schema change.
- All access is mediated by row-level security — see [security.md](security.md). Row-level enforcement is the real gate; UI gating is convenience only.
- Use the server-side [BACKEND_PLATFORM] client in server units and route handlers; the browser client only in client components that genuinely need it.

## API routes
- Resolve role once via the role helper; return `404` (not `403`) for unauthorized resources to avoid leaking existence.
- Every mutation appends to an audit log with actor id, action, target type, target id, and metadata. Tenant/org-scoped actions also emit org-level audit rows.
- Keep existing endpoint signatures stable; they resolve tenant/org context from the scope they target.

## AI behavior ([PROJECT_DOCTRINE]-critical)
- Apply [PROJECT_NAME]'s AI doctrine as defined in [domain-knowledge.md](../context/domain-knowledge.md) — keep the AI within its intended role (e.g. filter/judge vs. generator) and never let it exceed that scope.
- If the AI produces a confidence/quality score that gates an outcome, enforce the defined threshold strictly (no exceptions).
- Keep prompts in one documented location ([DOCS_DIR]/ai-prompts). AI logic is scoped to its tenant even if higher-tier admins can *view* results.
- Every AI call is logged to an AI call log (feeds health/observability views).

## Auth (locked)
- Use only the approved auth mechanism(s) for [PROJECT_NAME] (e.g. email + password with **mandatory** verification). No unapproved methods (magic links, OAuth, SSO) unless explicitly added.
- Invitations are token-based via a dedicated invitations table.
