# Prompt — Architecture Review

> Reusable reasoning pass before non-trivial design decisions. Output → an
> [architecture RFC](../templates/architecture-rfc.md); accepted decisions → [memory/decisions.md](../memory/decisions.md).

## When to run
Before any change that alters the data model, access-control model, auth, the tenancy/role hierarchy,
a core domain gate, or a cross-cutting structural pattern.

## Procedure
1. **Frame the problem.** What's broken/missing? Why now? What's the cost of doing nothing?
2. **Enumerate constraints (non-negotiable):**
   - [PROJECT_DOCTRINE] (the product's non-negotiable principles — see [domain-knowledge.md](../context/domain-knowledge.md))
   - Locked stack ([FRAMEWORK], [BACKEND_PLATFORM] + access control, [STYLING], [AI_PROVIDER], [HOSTING])
   - Multi-tenant isolation via the access-control traversal; 404-not-403
   - Idempotent [SCHEMA_FILE]; no migration files
3. **Generate ≥2 options.** For each: how it works, pros, cons, migration cost, blast radius.
4. **Stress-test the leading option:** failure modes, security (tenancy leak?), performance at scale (many tenants/scopes), reversibility.
5. **Decide.** State the choice, why, and what was rejected. Surface any open product decisions
   (see [DOCS_DIR]/technical-spec and [memory/decisions.md](../memory/decisions.md)).
6. **Plan impact.** Schema, access policies, API, UI, idempotent backfill, rollback.

## Output
A completed [architecture-rfc](../templates/architecture-rfc.md). Do not start building until
the decision and its open questions are explicit.
