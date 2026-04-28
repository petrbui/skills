# Example GapHunter Session — Senior Dev

This is what a GapHunter session looks like for a returning senior developer
using Deep Mode, the `vocab` command, and The Ambush.

---

## Dashboard (returning user)

**GapHunter:** Welcome back. 🔥 Day 4 streak.

```
★★★ Promises · event loop · CSS specificity
★★  useCallback · memoization
GAPS: React Suspense · Web Workers · WeakMap
```

2 concepts until The Ambush fires.

What do you want? `suggest` / `teach me X` / `vocab X` / `ambush me`

---

## Vocab Quick-Hit

**User:** vocab WeakMap

**GapHunter:** **WeakMap** — like a `Map`, but keys must be objects and
are held *weakly*: if the object has no other references, the
garbage collector can remove it and GapHunter automatically
cleans up the entry. No memory leak. No manual cleanup.

Use it when you need to attach private metadata to DOM nodes
or class instances without preventing garbage collection.

Not iterable — you can't loop over a WeakMap.

Want the full lesson? Type `teach me WeakMap`.

---

## Deep Mode Scan

**User:** deep scan

**GapHunter:** Scanning your TypeScript codebase via LSP…

Patterns found:
- `useCallback` on every render function — suggests you may not
  fully understand when memoization helps vs. hurts.
- Several `Promise.all` chains with no `.catch` — error handling
  gap likely.
- `as any` in 6 files — type safety awareness gap possible.

Top suggestion: **Promise error handling** — it's causing real
bugs in your code right now.

Type `suggest` to start there, or pick something else.

---

## Lesson: Promise Error Handling

**User:** teach me Promise error handling

**GapHunter:** ⚡ Dense mode — no hand-holding.

**The gap:**
`Promise.all` rejects fast — first rejection kills the whole batch.
Your other promises may still be running, their results silently dropped.

**The fix:**
```typescript
// ❌ First failure drops everything
const results = await Promise.all([fetchA(), fetchB(), fetchC()])

// ✅ Each settles independently
const results = await Promise.allSettled([fetchA(), fetchB(), fetchC()])
results.forEach(r => {
  if (r.status === 'fulfilled') use(r.value)
  if (r.status === 'rejected') log(r.reason)
})
```

**The subtlety:**
`allSettled` never rejects. You always get an array. The cost:
you must check `.status` on every result yourself. No free throw.

Explain back: when would you choose `Promise.all` over `Promise.allSettled`?

**User:** all when you want to fail fast — if one fails, you dont care about
the rest. allSettled when you want every result regardless of failures

**GapHunter:** ★★★ — exactly right. Fail-fast vs. collect-all.
That's the mental model, not just the API.

**Why this matters in your code:**
You have 6 unhandled Promise chains. `allSettled` on the
batch calls, `.catch` on the single ones. 10 minutes of fixes,
zero silent failures.

---

## The Ambush

**GapHunter:** ⚡ THE AMBUSH — Promise error handling (★★★)

*"You're running 3 parallel API calls with `Promise.all`.
Call B fails with a 429 rate limit. Call A completed.
Call C is mid-flight.*

*What happens? What does your code receive? What should
you have used instead?"*

**User:** Promise.all rejects immediately with the 429 from B.
A's result is discarded. C keeps running but nobody is
listening to it. We get nothing. Should have used allSettled —
each call settles independently and we keep A's data.

**GapHunter:** ★★★ confirmed. You got the ghost-promise too —
C keeps running unobserved. That's the detail most people miss.

🏆 **Achievement unlocked: Ghost Buster**
"You know about the promises nobody is watching."

---

## Session Export

**User:** export session

**GapHunter:**

```
# GapHunter Session — 2026-04-28

## Concepts Learned
- Promise error handling: Promise.all fails fast and discards results.
  Promise.allSettled collects everything. Choose based on whether partial
  success is useful.

## Key Insights
- Ghost promises: Promise.all rejection doesn't cancel in-flight calls —
  they complete silently, unobserved, wasting resources.
- allSettled never rejects — you always check .status yourself.

## Vocab
- WeakMap: object-keyed Map with weak references; GC-friendly private metadata.

## The Ambush Results
- Promise error handling: PASS — correctly identified ghost promise behaviour

## Still To Learn
- React Suspense · Web Workers · WeakMap (full lesson)
```

Paste into NotebookLM → ask it to quiz you → listen to the podcast.

🥇 **Achievement unlocked: The Archivist**
"You review. Most people just move on."
