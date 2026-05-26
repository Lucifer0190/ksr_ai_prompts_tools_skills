# Checklist — Security Review

> Tenant isolation is the product's core promise. Pairs with [rules/security.md](../rules/security.md).
> Run on any change touching data access, auth, access-control policies, or API routes.

## Tenancy / access control
- [ ] New/changed tables/resources enforce the tenant access model server-side
      ([describe your tenancy/authz model] — e.g. highest-tier-wins traversal, then per-resource role branch)
- [ ] Unauthorized access returns **404, not 403** (no existence leak)
- [ ] `[VIEWER_ROLE]` is read-only at **both** the data layer and the UI
- [ ] No client-only gating used as the sole access control

## Auth
- [ ] Only the approved auth mechanism(s) used; required verification still mandatory (no unapproved magic link/OAuth/SSO introduced)
- [ ] Invitation tokens validated server-side: token + role + expiry + single-use

## Secrets & data
- [ ] No secrets committed; server-only keys not exposed with the public client prefix
- [ ] Privileged/service-role keys stay server-side
- [ ] No secrets/tokens/customer PII logged to client-visible output or pushed to MCP servers

## Audit
- [ ] Every mutation writes an audit-log row (actor, action, target, metadata)
- [ ] Tenant/org-scoped actions emit org-level audit rows

## AI
- [ ] AI behavior stays within its defined role per [PROJECT_DOCTRINE] (no out-of-scope capability introduced)
- [ ] Any AI gating threshold logic intact
- [ ] AI calls logged to the AI call log
