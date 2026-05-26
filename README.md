# 🧠 KSR Prompt Repo

A personal collection of reusable **AI prompts, tools, and skills** for Claude Code and other AI development workflows.

## 📦 Contents

### 🏗️ [claude_md_organizer.md](claude_md_organizer.md)

A prompt that analyzes an existing `.claude/CLAUDE.md` setup and refactors it into a scalable, modular Claude Code "operating system" — splitting responsibilities across `rules/`, `commands/`, `workflows/`, `templates/`, `context/`, `checklists/`, `prompts/`, and `memory/`. Optimized for long-term autonomous development, MCP integrations, and Trello automation.

### 📋 [trello_manager_with_claude/](trello_manager_with_claude/)

A setup for letting Claude keep a **Trello board** synchronized with your development work, phase by phase.

| File | Purpose |
| --- | --- |
| 🗂️ [trello_manager.md](trello_manager_with_claude/trello_manager.md) | Trello project-management rules — card creation, naming, labels, checklists, and status flow (Backlog → In Progress → In Review). |
| ⚙️ [.mcp.json](trello_manager_with_claude/.mcp.json) | MCP server configuration for the Trello integration. |
| 📖 [README.md](trello_manager_with_claude/README.md) | Full setup instructions. |

**🚀 Quick start:**

1. 🔌 Place [.mcp.json](trello_manager_with_claude/.mcp.json) in your project root, then run and authenticate the MCP server.
2. 🗂️ Put [trello_manager.md](trello_manager_with_claude/trello_manager.md) in your `.claude/rules/` folder and reference it from `CLAUDE.md`.
3. 🎯 Set your board name and project name (the card title prefix), and optionally adjust the card flow (Backlog → In Progress → In Review).
4. 🛠️ Run your development phase by phase — Claude will keep the board updated as it works.
</content>
