---
name: review
description: Run a spaced-review session for the MIT Learning OS vault and update the review queue. Use for /review, "what's due", "quiz me on what I've learned".
---

# /review

Argument: optional concept/unit filter or max items. Rules in `.Codex/rules/` apply. Field definitions: `00-System/Conventions.md` (Spaced review).

## Steps

1. **Queue.** Skip `fixture: true` items. Scan `review-card` notes and `## Recall` blocks for `next_review <= today`. Regenerate `80-Learning/Reviews/queue.md` (sorted by due date, then by weak-area priority from recent errors).
2. **Ask.** One item at a time, active recall only: the user answers before seeing the reference answer.
3. **Grade** each: `again` / `hard` / `good` / `easy` (ask the user for self-grade when ambiguous, and give your own assessment).
4. **Update** scheduling fields with this rule:
   - `again`: `interval = 1`, `ease = max(1.3, ease - 0.2)`
   - `hard`: `interval = max(1, round(interval * 1.2))`, `ease = max(1.3, ease - 0.15)`
   - `good`: `interval = round(interval * ease)`
   - `easy`: `interval = round(interval * ease * 1.3)`, `ease = ease + 0.15`
   - new items start at `interval = 1`, `ease = 2.5`. `next_review = today + interval`.
5. **Log** misses as `error-entry` notes when they reveal a real gap, and link them to the concept.
6. **Update** `memory.md` review counts.

## Guardrails

- Only edit scheduling fields and the queue; do not change note content or status.
- This scheduling rule is the single definition; it is not repeated elsewhere. Changing it is a `/evolve` change.
