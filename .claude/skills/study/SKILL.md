---
name: study
description: Active-recall study session on a concept, derivation or course unit in the MIT Learning OS vault. Use for /study, "teach me", "help me understand", formula interpretation or derivation practice.
---

# /study

Mode (entry point). Argument: a concept, unit, or note (e.g. `/study Fisher information`).

1. Locate existing notes and weak points (`80-Learning/Errors/`, `memory.md`).
2. Run `socratic-tutor`: the user attempts before any explanation.
3. Run `formula-analysis` for formulas the session touches; `concept-builder` for missing or thin concept notes.
4. Hand mistakes to `error-analyzer`; add `review-card` notes for weak points.
5. Update `memory.md` if the focus changed.
