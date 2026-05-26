# Workflow — Code Review

> Procedure for reviewing changes. Invoked by `/review`. Read-only by default — report,
> don't edit, unless the user asks for fixes.

## 1. Scope the diff
- Determine target: PR number, branch, or current diff vs `main`. Use `gh` for PRs.
- Read the full diff plus the surrounding code it touches (don't review lines in isolation).

## 2. Review in priority order
1. **Doctrine** ([domain-knowledge](../context/domain-knowledge.md)): enforce [PROJECT_DOCTRINE] — the non-negotiable product invariants and any look-and-feel locks.
2. **Security & tenancy** ([security-review checklist](../checklists/security-review.md)): access-control traversal, 404-not-403, audit-log writes, [VIEWER_ROLE] read-only at the data layer + UI, no leaked secrets.
3. **Correctness**: logic, edge cases, error handling, race conditions (esp. realtime/multiplayer).
4. **Rules**: [coding](../rules/coding.md), [architecture](../rules/architecture.md), [backend](../rules/backend.md), [frontend](../rules/frontend.md), [ui-ux](../rules/ui-ux.md), [accessibility](../rules/accessibility.md), [performance](../rules/performance.md), [naming](../rules/naming.md).
5. **States & responsive**: loading/error/empty present; 375px clean; touch targets ≥44px.
6. **Tests/types**: [TYPECHECK_CMD], [LINT_CMD], build clean; doctrine-critical paths covered.

## 3. Report
- Each finding: `severity (blocker|major|minor|nit) — file:line — issue — fix`.
- Verdict: approve / approve-with-nits / request-changes, plus a one-paragraph summary.

## 4. After review
- If fixes are requested, switch to [bug-resolution](bug-resolution.md) or [feature-development](feature-development.md) as appropriate.
- Suggest `/ultrareview` to the user for a deeper multi-agent cloud pass (they must trigger it).
