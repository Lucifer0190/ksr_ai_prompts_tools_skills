# Rule — Coding

> Stable, language-level constraints for every [LANGUAGE]/[UI_LIBRARY] file touched in [PROJECT_NAME].
> Workflow logic lives in `.claude/workflows/`; this file is only *what* good code must be.

## [LANGUAGE]
- Keep the strictest available type-safety mode on (e.g. `"strict": true`). Never weaken the compiler/linter config. Avoid escape hatches like `any` — use a constrained unknown type + narrowing, or a real type.
- No type-suppression comments (e.g. `// @ts-ignore` / `// @ts-expect-error`) without a one-line justification comment.
- Type at boundaries: props/params shapes, API request/response, and [BACKEND_PLATFORM] row/record types ([SRC_DIR]/.../types).
- Match the surrounding file's idiom for declaring types (e.g. prefer inference-friendly union types and explicit shapes for props) — match the surrounding file.

## Class/style composition — one utility only
Compose [STYLING] classes through a single shared utility (e.g. a `cn()` helper combining a class-list builder + a merge/dedupe step). Never join classes with template literals or string concatenation.

```ts
// Example ([STYLING] + React): utils/cn.ts
import { clsx, type ClassValue } from 'clsx'
import { twMerge } from 'tailwind-merge'
export function cn(...inputs: ClassValue[]) {
  return twMerge(clsx(inputs))
}
```

```tsx
// ✅ Always
<div className={cn('px-4 py-2', isActive && 'bg-blue-500', className)} />
// ❌ Never
<div className={`px-4 py-2 ${isActive ? 'bg-blue-500' : ''}`} />
```

## General
- One primary unit (component/module) per file, exported clearly. Define its props/interface shape in the same file, above the unit.
- No hardcoded brand color values in components — use design-token references (fixed colors documented in [DESIGN_SYSTEM_REF]).
- Match the surrounding code's idiom, naming, and comment density. Don't introduce a new style locally.
- No dead code, no commented-out blocks left behind. Delete it; git remembers.
- If [FRAMEWORK] is pinned to a version that differs from common training data, read the installed framework docs (e.g. `node_modules/.../docs/`) before using its APIs — assume breaking changes.
