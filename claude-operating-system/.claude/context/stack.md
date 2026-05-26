# Context — Stack

> The actual installed stack (source: your dependency manifest, e.g. `package.json` /
> `pyproject.toml` / `go.mod`). Treat this as **ground truth** when it differs from prose docs.
> **Track any prose-vs-installed discrepancies in [memory/known-issues.md](../memory/known-issues.md).**
>
> Fill in every `[PLACEHOLDER]` below for your project. Delete categories that don't apply.

## Core
- **[FRAMEWORK] `[FRAMEWORK_VERSION]`** + **[UI_LIBRARY]** — record the *installed* version, not the version in tutorials.
  ⚠️ If the installed version differs from common training data, treat the framework as **non-standard**: read the locally installed docs (e.g. `node_modules/.../docs/`, the package's own `README`, or vendored docs) **before** writing framework/route/server code — assume breaking changes vs. what you "remember".
- **[LANGUAGE]** — keep the strictest type-safety / lint mode on (see [rules/coding.md](../rules/coding.md)).
- **[STYLING]** — note any constraints (e.g. "no component libraries", design tokens only).

## Data / auth
- **[DATABASE]** via **[BACKEND_PLATFORM]** — data layer + access model (note if row-level security / tenancy rules apply; see [rules/security.md](../rules/security.md)).
- **[AUTH_PROVIDER]** — authentication mechanism and any locked constraints (e.g. "email+password only, no OAuth").

## AI (if any)
- **[AI_PROVIDER]** — primary LLM/AI SDK and the pinned model id, if the product uses AI. If multiple providers are installed, note which code path uses which. Set to `none` if not applicable.

## Key libraries (usage rules: [rules/frontend.md](../rules/frontend.md))
> List your project's load-bearing libraries here, grouped by purpose, so the assistant uses
> the *installed* tool instead of improvising. Keep it short — only what shapes how code is written.
- **UI / components** — [list your UI primitives, component, or design-system libraries]
- **Forms / validation** — [list form + schema/validation libraries]
- **Data / tables / state** — [list data-fetching, table, or state libraries]
- **Animation / interaction** — [list animation, drag-drop, or realtime libraries]
- **Utilities** — [icons, class-composition, date, etc.]

## Tooling
- **Linter / formatter** — [tool + version], with any required plugins (e.g. accessibility lint).
- **Test framework** — **[TEST_FRAMEWORK]** for unit/e2e (see [rules/testing.md](../rules/testing.md)).
- **Package manager** — **[PACKAGE_MANAGER]**.
- **Standard commands** — build `[BUILD_CMD]`, test `[TEST_CMD]`, lint `[LINT_CMD]`, type-check `[TYPECHECK_CMD]`. Note any extras (seed, dev server, etc.).

## Install (reference)
See your dependency manifest for the authoritative list. Verify a dependency is actually present
before assuming it — prose docs drift from the real install.
