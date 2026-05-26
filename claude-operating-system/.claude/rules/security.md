# Rule — Security

> Tenant isolation is the product's core promise. The executable review is
> [.claude/checklists/security-review.md](../checklists/security-review.md).

## Tenancy & row-level security
- **Row-level security is the real enforcement layer.** UI hiding is convenience only — never the sole gate.
- Every table policy follows the tenant traversal (e.g. platform-admin OR org-admin-of-owning-org OR the per-resource role branch).
- Resolution rule (highest tier wins): [ADMIN_ROLE] → [MANAGER_ROLE] of the owning tenant → per-resource role → otherwise **404** (never reveal existence).
- Centralize checks in a single role helper ([SRC_DIR]/.../resolveRole); call once per request and trust the result. Provide guards (e.g. `requireAdmin`, `requireManager`).

## Auth (locked)
- Use only the approved auth mechanism(s) (e.g. email + password with mandatory verification). No unapproved methods (magic links, OAuth, SSO) unless explicitly added.
- Invitations are single-use tokens with an expiry; verify token, role, and expiry server-side before creating membership rows.

## Secrets & data
- Never commit secrets. Server-only env vars stay server-side; only explicitly public-prefixed vars reach the client. Confirm local env files are gitignored.
- Never log secrets, tokens, or full AI prompts containing customer data into client-visible output.
- Privileged/service-role keys are server-only; never expose them to the browser.

## Audit
- Every mutation writes to an audit log (actor id, action, target type, target id, metadata); tenant/org actions also emit org-scoped rows.

## Read-only role
- [VIEWER_ROLE] is read-only — enforce at **both** the data layer and the UI. Read-only users may see content for transparency but never write.
