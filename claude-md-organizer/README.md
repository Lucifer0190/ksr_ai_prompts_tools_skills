# 🪄 CLAUDE.md Organizer

A single, powerful **prompt** that analyzes a messy or monolithic `CLAUDE.md` and refactors it into a **scalable, modular Claude Code operating system** — the same structure shipped in [../claude-operating-system/](../claude-operating-system/).

> 💡 Use this when your `CLAUDE.md` has grown into a wall of mixed rules, context, and procedures and you want it split into clean, maintainable layers.

## ✨ What it does

Feed it your current setup and it produces:

- 🧭 A **minimal root `CLAUDE.md`** that only carries project identity, high-level principles, and `@`-imports/references to everything else.
- 📦 A full **`.claude/` folder** with responsibilities cleanly separated:

```
.claude/
├── rules/         📏 persistent behavioral constraints
├── commands/      ⌨️  reusable operations
├── workflows/     🔄 step-by-step autonomous procedures
├── templates/     📄 standard output structures
├── context/       📚 stable project knowledge
├── checklists/    ✅ validation gates
├── prompts/       💭 advanced reasoning passes
└── memory/        🧠 evolving project state
```

- 🔗 **MCP + Trello integration** logic extracted into dedicated modules.
- 📝 An explanation of **what moved and why**, plus suggestions for future scaling.

## 🎯 Design goals it optimizes for

- 🛠️ Maintainability & clarity
- ♻️ Reduced duplication
- 🧩 Clean separation of responsibilities
- 🤖 Autonomous, long-running development workflows
- 🔌 MCP-enabled tooling and Trello automation
- 📈 Scalability as the project grows — **while preserving all existing behavior and constraints**

## 🚀 How to use

1. 📂 Open [claude_md_organizer.md](claude_md_organizer.md) and copy its contents.
2. 💬 Paste it to Claude Code **inside the project whose `.claude/CLAUDE.md` you want to refactor** (so it can read your current setup).
3. 🔍 Review the proposed structure and generated files, then apply them.

> 🏗️ Prefer to start from a ready-made structure instead of generating one? Use [../claude-operating-system/](../claude-operating-system/) directly.
</content>
