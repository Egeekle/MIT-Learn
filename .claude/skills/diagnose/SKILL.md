---
name: diagnose
description: Analyse error entries, attempts and review history in the MIT Learning OS vault to diagnose knowledge gaps and recommend targeted practice. Use for /diagnose, "where am I weak", "why do I keep missing".
---

# /diagnose

Mode (entry point). Argument: optional concept/unit/time window.

1. Run `diagnostic` (it stops with an insufficient-data report if evidence is thin).
2. Optionally ask the user a few probing questions via `socratic-tutor` to separate competing hypotheses.
3. Propose the next `/study`, `/exercise` or `/review` targets from the report.
