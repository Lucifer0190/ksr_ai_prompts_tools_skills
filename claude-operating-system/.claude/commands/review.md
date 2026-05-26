---
description: Review pending changes against [PROJECT_NAME] rules, doctrine, and security
argument-hint: "[PR number | branch | empty for current diff]"
---

# /review

Review the changes in `$ARGUMENTS` (default: current branch diff vs `main`) by executing
[.claude/workflows/code-review.md](../workflows/code-review.md).

## What to check (in order)
1. **Doctrine.** Enforce [PROJECT_DOCTRINE] — the non-negotiable product invariants. See [domain-knowledge](../context/domain-knowledge.md).
2. **Security & tenancy.** [security-review checklist](../checklists/security-review.md) — access-control traversal, 404-not-403, audit rows, [VIEWER_ROLE] read-only.
3. **Rules compliance.** coding, architecture, backend, frontend, ui-ux, accessibility, performance, naming.
4. **States.** loading/error/empty present; mobile at 375px; touch targets ≥44px.
5. **Tests & types.** [TYPECHECK_CMD], [LINT_CMD], build clean; doctrine-critical paths covered.

## Output format
For each finding: `severity (blocker|major|minor|nit) — file:line — issue — suggested fix`.
End with a verdict (approve / approve-with-nits / request-changes) and a one-paragraph summary.
Do not modify code in review mode unless asked; report only.

> For a deeper multi-agent cloud review, tell the user to run `/ultrareview` (user-triggered, billed — you cannot launch it).
