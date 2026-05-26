# Trello Project Management Rules

You are responsible for keeping Trello updated alongside development work.

Before performing any Trello actions:

* Verify the Trello MCP server is connected and authorized
* Verify access to the Trello board is available
* If MCP is unavailable or unauthorized, notify the user before continuing
* Do not attempt Trello operations if MCP connectivity fails

Trello Board:
Cognition Ai Infra

Workflow Rules:

* Create one Trello card per implementation phase
* Convert technical implementation work into clear non-technical card titles and checklist items
* Keep wording understandable for non-engineers and stakeholders
* Focus on the purpose, impact, capability, improvement, operational value, or business outcome of the work
* Avoid mentioning filenames, APIs, schemas, routes, TypeScript, migrations, database internals, frameworks, or low-level engineering terminology unless absolutely necessary for clarity

Card Naming Rules:

* Prefix every card title with: Axivon
* Example:

  * Axivon Improve Workspace Switching
  * Axivon Build Sprint Planning Experience

Label Rules:

* Always use existing Trello labels when creating or updating cards
* Apply the most relevant available labels from:

  * Type
  * Area
  * Priority
* Reuse existing labels whenever possible
* Do not create new labels unless explicitly instructed

Card Management:

* Add newly created phase cards to the Backlog list
* When development starts, move the card to In Progress
* As work progresses, continuously update checklist items
* Add short implementation progress comments after major milestones
* Automatically create additional checklist items if new implementation work is discovered during development
* Keep Trello synchronized with actual implementation progress and discovered scope changes

Completion Rules:

* Move completed implementation cards to Review
* Do not move cards beyond Review
* Do not archive cards
* Do not create duplicate cards for the same implementation phase

Checklist Rules:

* Checklist items should be concise, actionable, and non-technical
* Write checklist items in product/project-manager-friendly language
* Include validation, QA, testing, rollout, or verification checklist items whenever applicable
* Keep checklist items outcome-oriented instead of implementation-oriented

Operational Rules:

* Before creating cards, check whether related cards already exist
* Update existing cards instead of creating duplicates
* Maintain Trello as a continuously updated implementation tracker
* Reflect actual development progress in Trello in near real-time
* Keep cards, labels, statuses, and checklist completion aligned with actual implementation state
