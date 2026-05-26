# 🗺️ [PROJECT_NAME] `.claude/` Operating System

Modular Claude Code configuration. The auto-loaded entry point is the **repo-root `CLAUDE.md`**
(Claude Code only auto-loads root `CLAUDE.md` and `~/.claude/CLAUDE.md`). The root file carries
project identity + operating principles, `@`-imports the always-on layers (`rules/`, key
`context/`), and references the on-demand layers below.

## 🧩 Layers

| Folder | Purpose | Loaded |
|---|---|---|
| 📏 `rules/` | Persistent behavioral constraints (stable, no workflow logic) | **Always** (`@`-imported by root) |
| 📚 `context/` | Stable project knowledge (stack, domain, architecture, glossary) | Always for stack/domain/glossary; product/architecture on demand |
| ⌨️ `commands/` | Slash commands defining execution flow + outputs | On demand (`/name`) |
| 🔄 `workflows/` | Step-by-step autonomous procedures with [PM_TOOL] sync | On demand |
| 📄 `templates/` | Reusable output structures (PR, RFC, changelog, plans) | On demand |
| ✅ `checklists/` | Executable verification gates | On demand (before "done") |
| 💭 `prompts/` | Reusable advanced reasoning passes | On demand |
| 🧠 `memory/` | Evolving project state (issues, debt, roadmap, decisions, anti-patterns) | On demand (read before big changes) |
| 🎨 `skills/` | Reusable design/build skill definitions | Per Claude Code |
| ⚙️ `settings.local.json` | Example permission allowlist | Per Claude Code |

## 🗂️ Map
```
CLAUDE.md (repo root — orchestrator, auto-loaded)
.claude/
├── README.md                  ← this file
├── rules/        coding, architecture, backend, frontend, ui-ux, accessibility,
│                 security, testing, git, naming, performance, trello, mcp
├── commands/     create-feature, bugfix, refactor, review, sprint-plan, release
├── workflows/    feature-development, bug-resolution, code-review,
│                 deployment, release-process, sprint-management
├── templates/    pr-template, bug-report, changelog, sprint-plan,
│                 architecture-rfc, implementation-plan
├── context/      product-overview, architecture-overview, domain-knowledge, stack, glossary
├── checklists/   qa, accessibility, security-review, deployment, pre-release
├── prompts/      pm-conversion, architecture-review, optimization, deep-debugging
└── memory/       known-issues, tech-debt, roadmap, decisions, avoided-patterns
```

## 📐 Conventions
- **Rules** = constraints (what must always be true). **Workflows** = procedures (how to do a job).
  **Commands** = entry points that invoke workflows. **Checklists** = verification. **Prompts** =
  reasoning systems. **Context** = knowledge. **Memory** = evolving state. Keep these separate.
- Cross-reference with relative markdown links; don't duplicate content across files.
- Detailed product/engineering docs remain in your repo's `[DOCS_DIR]/` — context files point to them.

## 📈 Scaling guidance
- New constraint → add/extend a `rules/` file (keep each focused; split when a file covers two concerns).
- New repeatable job → add a `workflows/` file + a thin `commands/` entry point.
- New standard artifact → add a `templates/` file.
- New domain area → add a `context/` file; `@`-import it from root only if it must always be in context.
- Keep the always-on footprint small: prefer on-demand references over new `@`-imports.
- As tenants/features grow, consider sub-folders (e.g. `rules/frontend/`, `context/integrations/`).
