# CLAUDE.md — [PROJECT_NAME] Operating System

> **Entry point.** Claude Code auto-loads this root file at session start. It is an
> orchestrator: it carries project identity, top-level operating principles, and
> `@`-imports the always-on rule and context layers. Everything else lives in
> `.claude/` and is loaded on demand.
>
> **Why this file is at the repo root (not `.claude/CLAUDE.md`):** Claude Code only
> auto-loads `CLAUDE.md` from the project root and `~/.claude/`. Keeping the
> orchestrator here guarantees it is always in context. All *modules* live under
> `.claude/`. See `.claude/README.md` for the full map.
>
> **📌 Template note:** every `[SQUARE_BRACKET]` value is a placeholder — see
> [PLACEHOLDERS.md](PLACEHOLDERS.md) and find-and-replace across this folder to adapt
> the system to your project. Anything still bracketed after setup is unfinished.

---

## 1. Project identity

- **Name**: [PROJECT_NAME]
- **Type**: [PROJECT_TYPE]
- **What it does**: [PROJECT_TAGLINE]
- **Language**: [LANGUAGE]
- **Framework**: [FRAMEWORK] — **see [stack](.claude/context/stack.md) for the *installed* version; if it differs from common training data, read the local `node_modules`/vendor docs before writing framework code.**
- **UI / Styling**: [UI_LIBRARY] + [STYLING]
- **Data / Auth**: [BACKEND_PLATFORM] ([DATABASE] + [AUTH_PROVIDER])
- **AI** (if any): [AI_PROVIDER]
- **Hosting**: [HOSTING]

Full product doctrine: [.claude/context/product-overview.md](.claude/context/product-overview.md) and your `[DOCS_DIR]/`.

---

## 2. Operating principles (read before acting)

1. **Doctrine first.** Honor [domain doctrine](.claude/context/domain-knowledge.md) — your product's non-negotiable rules — over convenience. Never violate it silently.
2. **Rules are non-negotiable.** The `@`-imported rule files below are hard constraints, not suggestions. When a rule and a request conflict, surface the conflict — do not silently break the rule.
3. **Match the codebase.** Follow the architecture, conventions, and idioms already in use (see [architecture](.claude/rules/architecture.md) and [naming](.claude/rules/naming.md)). Don't introduce a new local style.
4. **Accessibility and responsiveness are acceptance criteria**, not polish. A feature that fails [accessibility](.claude/checklists/accessibility.md) or breaks on small screens is unfinished.
5. **Keep [PM_TOOL] in sync.** Project-management mirroring is part of the work, not an afterthought — follow the [sprint-management workflow](.claude/workflows/sprint-management.md). Verify [MCP connectivity](.claude/rules/mcp.md) first.
6. **Self-audit before claiming done.** Run the relevant [checklist](.claude/checklists/) and report results honestly. "Done" means verified, not written.
7. **Prefer modules over re-deriving.** Use the workflow/command/template that already encodes the procedure rather than improvising.

---

## 3. Always-on layers (imported)

### Rules — persistent behavioral constraints
@.claude/rules/coding.md
@.claude/rules/architecture.md
@.claude/rules/backend.md
@.claude/rules/frontend.md
@.claude/rules/ui-ux.md
@.claude/rules/accessibility.md
@.claude/rules/security.md
@.claude/rules/testing.md
@.claude/rules/git.md
@.claude/rules/naming.md
@.claude/rules/performance.md
@.claude/rules/trello.md
@.claude/rules/mcp.md

### Context — stable project knowledge
@.claude/context/stack.md
@.claude/context/domain-knowledge.md
@.claude/context/glossary.md

> `context/product-overview.md` and `context/architecture-overview.md` are larger and
> referenced on demand rather than imported, to keep the always-on context lean.

---

## 4. On-demand layers (reference by path, not imported)

Load these when the task calls for them:

| Layer | Path | Use when |
|---|---|---|
| **Commands** | `.claude/commands/` | A named operation is requested (`/sprint-plan`, `/create-feature`, `/release`, `/bugfix`, `/refactor`, `/review`). These are real Claude Code slash commands. |
| **Workflows** | `.claude/workflows/` | Executing a multi-step process end to end (feature, bug, deploy, release, review, sprint mgmt). |
| **Templates** | `.claude/templates/` | Producing a standard artifact (PR body, bug report, changelog, sprint plan, RFC, implementation plan). |
| **Checklists** | `.claude/checklists/` | Verifying quality before marking work done (pre-release, QA, a11y, security, deploy). |
| **Prompts** | `.claude/prompts/` | Running a reusable advanced reasoning pass (PM conversion, architecture review, optimization, deep debugging). |
| **Memory** | `.claude/memory/` | Recording or recalling evolving project state (known issues, tech debt, roadmap, decisions, avoided patterns). **Read `decisions.md` and `avoided-patterns.md` before large changes.** |

---

## 5. Definition of done

A unit of work is complete only when:
1. The relevant **rules** were followed (or conflicts surfaced).
2. The matching **checklist** passes.
3. **[PM_TOOL]** reflects the real state (card moved, checklist items ticked, progress comment added).
4. Any new **decision, debt, or avoided pattern** is written to `.claude/memory/`.
</content>
