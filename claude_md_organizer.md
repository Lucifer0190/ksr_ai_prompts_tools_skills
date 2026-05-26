Analyze my entire current `.claude/CLAUDE.md` setup and refactor it into a scalable, modular Claude Code operating system optimized for long-term autonomous development workflows.

Goals:

* Improve maintainability
* Improve clarity
* Reduce duplication
* Separate responsibilities cleanly
* Support autonomous development workflows
* Support MCP integrations
* Support Trello project management automation
* Preserve all current behavior and operational constraints
* Keep the system scalable as the project grows

Target Architecture:

```
.claude/
├── CLAUDE.md
├── rules/
├── commands/
├── workflows/
├── templates/
├── context/
├── checklists/
├── prompts/
└── memory/
```

Requirements:

1. Root CLAUDE.md

* Keep minimal and orchestration-focused
* Only include:

  * project identity
  * high-level operating principles
  * imports/references to other files
* Use modular references like:

  ```
  @./rules/coding.md
  @./workflows/feature-development.md
  ```

2. rules/
   Move persistent behavioral constraints into categorized rule files.

Examples:

* coding.md
* architecture.md
* backend.md
* frontend.md
* ui-ux.md
* security.md
* testing.md
* git.md
* naming.md
* performance.md
* trello.md
* mcp.md

Rules should:

* contain stable constraints
* avoid workflow-specific logic
* avoid duplication
* use concise actionable instructions

3. commands/
   Create reusable operational command files.

Examples:

* sprint-plan.md
* create-feature.md
* release.md
* bugfix.md
* refactor.md
* review.md

Commands should:

* define execution flow
* define expected outputs
* define automation behavior
* define tool usage expectations

4. workflows/
   Create step-by-step autonomous execution workflows.

Examples:

* feature-development.md
* bug-resolution.md
* deployment.md
* release-process.md
* code-review.md
* sprint-management.md

Workflows should:

* explain sequencing
* explain transitions
* explain update behavior
* include Trello synchronization behavior where applicable

5. templates/
   Extract reusable output/document structures.

Examples:

* pr-template.md
* bug-report.md
* changelog.md
* sprint-plan.md
* architecture-rfc.md
* implementation-plan.md

Templates should:

* standardize outputs
* improve consistency
* reduce prompt repetition

6. context/
   Extract stable project knowledge.

Examples:

* product-overview.md
* architecture-overview.md
* domain-knowledge.md
* stack.md
* glossary.md

Context files should:

* improve Claude’s decision quality
* explain business/domain concepts
* contain reusable project understanding

7. checklists/
   Create operational validation checklists.

Examples:

* pre-release.md
* qa.md
* accessibility.md
* security-review.md
* deployment.md

Checklists should:

* be executable by Claude
* support autonomous verification
* support repeatable quality control

8. prompts/
   Extract reusable advanced prompting systems.

Examples:

* pm-conversion.md
* architecture-review.md
* optimization.md
* deep-debugging.md

Prompts should:

* improve reusable task quality
* reduce repetitive prompting effort

9. memory/
   Create persistent evolving project state tracking.

Examples:

* known-issues.md
* tech-debt.md
* roadmap.md
* decisions.md
* avoided-patterns.md

Memory files should:

* preserve long-term context
* track evolving project state
* help avoid repeated mistakes

10. Trello + MCP Integration
    Extract all Trello and MCP operational logic into dedicated modular files.

Requirements:

* Verify MCP connection before Trello operations
* Keep Trello synchronized with implementation progress
* Use existing labels automatically
* Create/update cards phase-wise
* Use non-technical PM-friendly wording
* Prefix card names with [project_name]
* Move cards only until Review
* Avoid duplicate cards
* Maintain checklist progress during development

11. Refactoring Rules

* Preserve ALL existing important instructions
* Do not oversimplify
* Do not silently remove operational constraints
* Remove duplicate instructions
* Normalize formatting and markdown structure
* Improve readability
* Improve scalability
* Group related concepts logically
* Add comments explaining purpose of each file
* Recommend additional folders/files if beneficial

12. Output Requirements
    Provide:

* proposed folder structure
* complete new root CLAUDE.md
* all extracted files with content
* explanation of what was moved and why
* suggestions for future scaling

13. Important Constraints

* Optimize specifically for Claude Code workflows
* Optimize for MCP-enabled autonomous development
* Optimize for long-running software projects
* Keep instructions execution-oriented instead of descriptive
* Maintain compatibility with VSCode Claude Code extension workflows
* Maintain compatibility with future automation and agent-style workflows
