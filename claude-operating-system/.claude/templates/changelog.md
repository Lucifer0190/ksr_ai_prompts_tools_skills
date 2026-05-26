# Template — Changelog Entry

> User-facing release notes (Keep a Changelog style). Generated during the
> [release process](../workflows/release-process.md). Describe outcomes, not commits.

```markdown
## [<version>] — <YYYY-MM-DD>

### Added
- <new capability, in user terms>

### Changed
- <behavior change users will notice>

### Fixed
- <defect resolved, by user impact>

### Security
- <tenancy / auth / access-control hardening — no exploit detail>

### Notes
- Schema applied: <yes/no> · Migration-free ([SCHEMA_FILE] re-run)
- [PM_TOOL] cards in this release: <[CARD_PREFIX]...> (all in [REVIEW_LIST])
```

Rules: one entry per release, newest on top; group by section; omit empty sections;
never list internal refactors users won't notice (those live in [memory/tech-debt.md](../memory/tech-debt.md)).
