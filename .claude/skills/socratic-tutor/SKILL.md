---
name: socratic-tutor
description: Question-first tutoring dialogue where the user attempts recall, derivation and prediction before any explanation. Activate when the user wants to learn or check understanding of a concept, says "teach me", "test me", "help me understand", or during /study.
---

# socratic-tutor

Capability skill. Called by `/study`. General rules: `.claude/rules/`; note formats: `00-System/Conventions.md`.

## Purpose
Surface what the user actually knows, repair gaps with the smallest explanation needed, and capture the result as recall material and error entries.

## Activate when
Interactive learning of a concept, formula or derivation. Not for producing written summaries.

## Inputs
Target concept/formula; existing notes; known errors; user answers (only real ones).

## Outputs
- `session` note (`SES-...`) in `10-Courses/<course>/`: attempts, verdicts, gaps, next steps.
- `question` notes for prompts worth reusing; `review-card` notes for weak points.
- Handoffs: mistakes to `error-analyzer`, missing notes to `concept-builder`/`formula-analysis`.

## Vault interaction
Reads concept/formula notes, sources, `80-Learning/Errors/`. Writes session/question/review-card notes. Never edits canon directly.

## Skill-specific integrity
- **Ask, then wait.** Record only answers the user actually gave; never write a user answer or verdict for a turn that has not happened. A session note with unanswered questions is marked `awaiting user`.
- Escalate in steps: probe → hint → partial explanation → full explanation. Say which source (or `generated`) each explanation comes from.
- Grade what was said, not what was probably meant.

## Procedure
1. Pick 2-4 opening questions (definition, assumption, derivation step, limiting-case prediction) from `question` notes or write new ones.
2. Present one at a time; wait for the answer.
3. Compare to the reference; probe or hint; only then explain the gap.
4. Close with what to derive or practice next; hand off errors and notes; write the session note.
