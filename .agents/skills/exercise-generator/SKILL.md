---
name: exercise-generator
description: Generate tiered practice exercises and question notes for a concept or formula, with hints, verified solutions and rubrics. Activate when the user asks for problems, quizzes or practice, or after a diagnostic identifies a gap to drill.
---

# exercise-generator

Capability skill. Called by `/exercise`. General rules: `.Codex/rules/`; formats: `00-System/Conventions.md`.

## Purpose
Produce problems that force recall, derivation, interpretation and transfer, targeted at known weak points.

## Activate when
Practice material is needed. Check `80-Learning/Errors/` and `80-Learning/Diagnostics/` to target it.

## Inputs
Concept/formula notes, difficulty, count, kind (derivation / interpretation / computation / conceptual / implementation).

## Outputs
- `exercise` notes (`EX-...`) in `40-Exercises/generated/`.
- `question` notes (`QST-...`) in `40-Exercises/questions/` for short recall/interpretation prompts.
Hints tiered nudge → structure → key step; solutions in collapsed callouts.

## Vault interaction
Reads concept/formula notes and error history; writes exercises/questions; links each to its concept. Does not write attempts (those come from the user) and does not touch canon notes.

## Skill-specific integrity
- Generated items are `source_type: generated`. Items transcribed from MIT or the user get a source record and their own label; never present generated problems as MIT problems.
- Every solution is verified before it is written (independent derivation or remote computation) and the verification method is stated in the note.
- Do not reveal solutions or answers in the presented problem text.

## Procedure
1. Choose targets and levels from the concept, its assumptions, and error history.
2. Write problems; include one transfer problem (new setting) per set.
3. Solve independently; record verification method.
4. Write hints, rubric, misconceptions; create the notes; report the set without solutions.
