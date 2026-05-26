# 📋 Trello Manager with Claude

Let Claude keep your **Trello board** synchronized with your development work — automatically creating, updating, and moving cards phase by phase as it codes.

## ✨ What it does

- 🃏 Creates one Trello card per implementation phase
- 🗣️ Converts technical work into clear, non-technical card titles and checklists
- 🏷️ Reuses your existing labels (Type, Area, Priority)
- ✅ Keeps checklist items updated as work progresses
- 🔄 Moves cards through your flow: **Backlog → In Progress → In Review**
- 💬 Adds short progress comments after major milestones

## 📁 Files

| File | Purpose |
| --- | --- |
| 🗂️ [trello_manager.md](trello_manager.md) | The Trello project-management rules Claude follows — card creation, naming, labels, checklists, and status flow. |
| ⚙️ [.mcp.json](.mcp.json) | MCP server configuration for the Trello integration. |

## 🚀 Setup

### 1️⃣ Add the MCP server

Place [.mcp.json](.mcp.json) in your **project root**, then run and authenticate the MCP server so Claude can talk to Trello.

```json
{
  "mcpServers": {
    "trello": {
      "type": "http",
      "url": "https://mcpfortrello.com/mcp"
    }
  }
}
```

### 2️⃣ Add the Trello manager rules

Copy [trello_manager.md](trello_manager.md) into your project's `.claude/rules/` folder and reference it from your `CLAUDE.md` so the rules load on every session.

### 3️⃣ Configure your board & project

[trello_manager.md](trello_manager.md) uses `[SQUARE_BRACKET]` placeholders. Find-and-replace them with your values:

- 🎯 `[BOARD_NAME]` — the Trello board to manage
- 🏷️ `[CARD_PREFIX]` — the prefix added to every card title (e.g. `Acme `)
- 🔄 `[BACKLOG_LIST]` / `[IN_PROGRESS_LIST]` / `[REVIEW_LIST]` — your board's column/list names (defaults: Backlog → In Progress → Review)

### 4️⃣ Develop phase by phase

Run your development work as usual. Claude will keep the board in sync — creating cards, updating checklists, posting progress, and moving cards up to **Review** in near real-time.

## ⚠️ Notes

- 🔌 Claude verifies the MCP connection before any Trello action and will notify you if it's unavailable.
- 🛑 Cards are never moved beyond **Review** and are never archived automatically.
- 🚫 Existing cards are updated instead of creating duplicates.
