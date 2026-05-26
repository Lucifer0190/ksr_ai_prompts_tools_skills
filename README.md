# 🧠 KSR AI Prompts, Tools & Skills

A collection of **reusable, project-agnostic building blocks** for working efficiently with AI coding tools (Claude Code and friends). Everything here is a **template** — fill in the `[SQUARE_BRACKET]` placeholders and drop it into your own project.

> 🎯 **Goal:** give anyone a clean starting point to set up a proper, scalable AI-assisted development system — instead of wiring it up from scratch every time.

## 📦 Modules

| Module | What it gives you |
|---|---|
| 🏗️ [claude-operating-system/](claude-operating-system/) | A complete, modular Claude Code "operating system" — a root `CLAUDE.md` orchestrator plus a `.claude/` tree of rules, commands, workflows, templates, context, checklists, prompts, memory, and skills. **Stack-agnostic**, driven by placeholders. |
| 🪄 [claude-md-organizer/](claude-md-organizer/) | A prompt that takes an existing, messy `CLAUDE.md` and **refactors it into the modular structure above**. Use it to generate or reorganize your own operating system. |
| 📋 [trello-manager/](trello-manager/) | A lightweight, drop-in rule + MCP config that lets Claude keep a **Trello board** synchronized with your development, phase by phase. |

## 🚀 Getting started

### 🏗️ Want a full AI operating system for your project?
Go to [claude-operating-system/](claude-operating-system/). Copy `CLAUDE.md` and the `.claude/` folder into your project root, then find-and-replace the placeholders listed in [claude-operating-system/PLACEHOLDERS.md](claude-operating-system/PLACEHOLDERS.md).

### 🪄 Already have a `CLAUDE.md` you want to clean up?
Use the prompt in [claude-md-organizer/](claude-md-organizer/) to refactor it into the modular layout.

### 📋 Just want Trello kept in sync?
Use [trello-manager/](trello-manager/) on its own — no full operating system required.

## 🔤 The placeholder convention

Every project-specific value is written as `[SQUARE_BRACKETS]` — e.g. `[PROJECT_NAME]`, `[FRAMEWORK]`, `[BOARD_NAME]`. Find-and-replace them to adapt a module to your project. Anything still bracketed after setup is something you still need to fill in. The operating system ships a full reference at [claude-operating-system/PLACEHOLDERS.md](claude-operating-system/PLACEHOLDERS.md).
</content>
