# Rule — Git

> Version-control hygiene. Commit/PR *procedure* lives in
> [.claude/workflows/release-process.md](../workflows/release-process.md); this is the standing policy.

## Branching
- Never commit directly to `main`. Branch first: `feat/...`, `fix/...`, `refactor/...`, `chore/...`, `docs/...`.
- One logical change per branch; keep PRs reviewable.

## Commits
- Conventional Commits: `type(scope): summary` (e.g. `feat(billing): add usage-based pricing tiers`).
- Imperative, present tense. Explain *why* in the body when non-obvious.
- Commit or push **only when the user asks.** Never `--no-verify`, never bypass signing, unless explicitly told.
- End commit messages with the co-author trailer the harness requires.

## Pull requests
- Use the [PR template](../templates/pr-template.md).
- PRs target `main` unless told otherwise. Use the `gh` CLI for GitHub operations.
- Link the [PM_TOOL] card and tick its checklist items in the PR body where relevant.

## Safety
- Avoid destructive ops (`reset --hard`, `push --force`, `checkout --`) unless clearly the best option and the user is aware.
- Don't delete/overwrite files you didn't create without surfacing what you found first.
