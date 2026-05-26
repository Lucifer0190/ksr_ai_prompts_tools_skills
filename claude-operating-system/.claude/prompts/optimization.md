# Prompt — Optimization

> Reusable pass for performance/quality improvement without changing behavior.
> Pairs with [rules/performance.md](../rules/performance.md). Record debt paid in
> [memory/tech-debt.md](../memory/tech-debt.md).

## Principle
Measure before optimizing. No speculative optimization — find the real cost first.

## Procedure
1. **Establish the baseline.** What's slow/heavy, and by what measure (bundle size, query time, render count, TTFB)? Capture numbers.
2. **Locate the dominant cost.** Profile, don't guess: client waterfalls, N+1 [DATABASE] queries, oversized client bundles, missing suspense boundaries, unmemoized hot paths, layout shift, slow AI calls blocking UI.
3. **Apply the smallest effective fix:**
   - Move work to the server; shrink the client-component boundary.
   - Narrow queries to the columns/rows needed; batch reads; paginate server-side.
   - Stream with suspense + skeletons; reserve heights to kill CLS.
   - Make AI/long calls non-blocking with optimistic/pending UI.
4. **Verify equivalence.** Behavior unchanged; type-check / lint / build green ([TYPECHECK_CMD], [LINT_CMD], [BUILD_CMD]); re-measure to prove the win.

## Output
Before/after numbers, the change made, and a one-line entry in [tech-debt.md](../memory/tech-debt.md)
if this revealed or paid down structural debt.
