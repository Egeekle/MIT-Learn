---
name: exercise
description: Generate, present and grade practice problems for a concept in the MIT Learning OS vault, with hints before solutions and error logging. Use for /exercise, "give me problems", "quiz me", "check my solution".
---

# /exercise

Mode (entry point). Argument: concept/unit, optional difficulty or count.

1. Run `exercise-generator` (targeted at known weak points); present without solutions; hints only on request.
2. The user answers; save an `exercise-attempt` note in `40-Exercises/attempts/`; grade step by step, marking unclear steps uncertain.
3. Run `error-analyzer` for each mistake; add `review-card` notes for missed points.
