# Context — Domain Knowledge (Doctrine)

> Your product's non-negotiable rules. Violating these is a bug even if the code is correct.
> Full narrative: [.claude/context/product-overview.md](product-overview.md) and `[DOCS_DIR]/product-overview`.
>
> This file holds **[PROJECT_DOCTRINE]** — the small set of principles that define what
> [PROJECT_NAME] *is* and refuse to compromise on. Keep it short and absolute. If a rule here
> conflicts with a request, surface the conflict; don't silently break it. Replace every
> bracketed slot with your own doctrine and delete sections that don't apply.

## The one question
> The single question your product exists to answer (its reason to exist, not a feature list).
**[PROJECT_NAME] answers: "[the core question your product answers]"** — not "[the thing competitors measure instead]".

## Core principles
> 2–4 load-bearing principles. Each should be a rule a contributor could *violate*, stated plainly.
1. **[PRINCIPLE_1]** — [one or two sentences on what it means in practice].
2. **[PRINCIPLE_2]** — [one or two sentences].
3. **[PRINCIPLE_3]** — [one or two sentences].

## Hard mechanics (do not violate)
> Concrete, checkable invariants derived from the principles above — thresholds, gates,
> states, and look-and-feel locks. Be specific enough to verify in code/UI.
- [Invariant 1 — e.g. a named threshold or status transition that must hold.]
- [Invariant 2 — e.g. a capability the system must never have.]
- [Invariant 3 — e.g. a UI/UX lock, such as fixed background, max width, or "not dark mode".]

## Core lifecycle (if your product has one)
> If your domain has a primary state machine or flow, sketch it as a fenced diagram.
```
[state A] → [state B] → [decision point] → ([branch 1] | [branch 2]) → [terminal state]
```

## What it is NOT
> Naming the adjacent things you are deliberately *not* is often the clearest doctrine.
[PROJECT_NAME] is not [adjacent category 1]. Not [adjacent category 2]. Not [anti-pattern you reject].

## North star
> One sentence describing success — the outcome that proves the system worked.
[The single-sentence outcome that means the product did its job.]
