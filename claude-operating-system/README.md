# 🏗️ Claude Operating System

A complete, **modular Claude Code configuration** you can drop into any project. It turns a single sprawling `CLAUDE.md` into a maintainable system: a thin orchestrator at the root plus a `.claude/` tree where each concern lives in its own focused file.

> 🧩 **Stack-agnostic by design.** Every project-specific value is a `[SQUARE_BRACKET]` placeholder. Adapt it to *your* language, framework, database, and product in minutes — see [PLACEHOLDERS.md](PLACEHOLDERS.md).

## 📁 What's inside

```
claude-operating-system/
├── CLAUDE.md          🧭 Root orchestrator (auto-loaded by Claude Code)
├── PLACEHOLDERS.md    🔤 Every placeholder + its meaning
└── .claude/
    ├── README.md      🗺️  Map of the whole tree
    ├── rules/         📏 Always-on behavioral constraints (coding, security, git, a11y…)
    ├── context/       📚 Stable project knowledge (stack, domain doctrine, glossary…)
    ├── commands/      ⌨️  Slash commands (/create-feature, /bugfix, /release…)
    ├── workflows/     🔄 Step-by-step procedures (feature, bug, deploy, release…)
    ├── templates/     📄 Reusable outputs (PR body, RFC, changelog, bug report…)
    ├── checklists/    ✅ Verification gates (QA, a11y, security, deploy, pre-release)
    ├── prompts/       💭 Advanced reasoning passes (architecture review, debugging…)
    ├── memory/        🧠 Evolving project state (decisions, tech debt, roadmap…)
    └── skills/        🎨 Reusable design/build skills
```

## 🧠 How it works

- 🧭 **`CLAUDE.md`** sits at the project root — Claude Code only auto-loads `CLAUDE.md` from the root (and `~/.claude/`). It carries project identity, top-level principles, and `@`-imports the always-on **rules** and key **context**.
- 📏 **Rules** = constraints (what must always be true). 🔄 **Workflows** = procedures (how to do a job). ⌨️ **Commands** = entry points that invoke workflows. ✅ **Checklists** = verification. 💭 **Prompts** = reasoning systems. 📚 **Context** = knowledge. 🧠 **Memory** = evolving state.
- 🪶 Everything except the always-on layers is loaded **on demand**, keeping the live context lean.

See [.claude/README.md](.claude/README.md) for the full layer map and scaling guidance.

## 🚀 Setup

1. 📋 **Copy** `CLAUDE.md` and the `.claude/` folder into the **root of your project**.
2. 🔤 **Open** [PLACEHOLDERS.md](PLACEHOLDERS.md) and find-and-replace every `[SQUARE_BRACKET]` across the copied files with your project's real values (name, stack, roles, board, commands…).
3. 📚 **Fill in the context skeletons** — `context/stack.md`, `context/domain-knowledge.md`, and `context/glossary.md` are intentionally blank templates describing *your* product doctrine, vocabulary, and stack.
4. 🧠 **Start fresh in `memory/`** — those files begin empty; Claude appends decisions, tech debt, and known issues as the project evolves.
5. ✅ **Verify** nothing is still bracketed (a quick search for `[` catches anything you missed), then start working.

## 🪄 Don't want to fill it in by hand?

The [claude-md-organizer](../claude-md-organizer/) prompt can generate this exact structure from an existing `CLAUDE.md`, or help you reorganize one you already have.
</content>
