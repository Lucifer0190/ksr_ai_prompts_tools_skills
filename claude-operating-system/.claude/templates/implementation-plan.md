# Template — Implementation Plan

> Produced in the plan step of [feature-development](../workflows/feature-development.md) and
> `/create-feature`. Keep it concrete and ordered.

```markdown
## Plan: <feature>

### Goal & acceptance criteria
- Goal: <what the user can do after this>
- Done when: <observable criteria>

### Doctrine fit
<how this respects [PROJECT_DOCTRINE]; flag any tension before building>

### Affected surfaces
- Routes: <pages + loading/error states>
- Server/Client split: <what stays server-rendered, what needs a client boundary and why>
- Libs: <[BACKEND_PLATFORM], AI, access policies, components touched>

### Steps (ordered, each independently verifiable)
1. <schema / types if needed — [SCHEMA_FILE], regenerate types>
2. <server data fetch + role resolution>
3. <UI: states (loading/error/empty), responsive, a11y>
4. <tests: doctrine-critical path + role isolation>

### [PM_TOOL]
- Card: [CARD_PREFIX]<title> · phase checklist items: <list>

### Risks / unknowns
<what might force a re-plan>

### Out of scope
<explicitly excluded, to prevent scope creep>
```
