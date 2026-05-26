# Template — Architecture RFC

> For non-trivial design decisions. Produced via [architecture-review](../prompts/architecture-review.md).
> Once accepted, record the outcome in [memory/decisions.md](../memory/decisions.md).

```markdown
## RFC: <title>
- Status: <draft | proposed | accepted | superseded>
- Date: <YYYY-MM-DD>
- Author: <name>

### Problem
<what's broken or missing; why now>

### Constraints (non-negotiable)
- Doctrine: [PROJECT_DOCTRINE] — the core product principles this decision must respect
- Stack locked: [FRAMEWORK], [BACKEND_PLATFORM] + [DATABASE], [STYLING], [AI_PROVIDER], [HOSTING]
- Tenancy/authz model: [describe your tenancy/authz model]

### Options considered
1. **<option>** — pros / cons / cost
2. **<option>** — pros / cons / cost

### Decision
<chosen option and why; explicitly note rejected options>

### Impact
- Schema ([SCHEMA_FILE]): <changes>
- Authz / access model: <changes>
- API surface: <changes>
- Migration/backfill: <idempotent steps>

### Risks & rollback
<what could go wrong; how to undo>

### Open questions
<anything needing a product call>
```
