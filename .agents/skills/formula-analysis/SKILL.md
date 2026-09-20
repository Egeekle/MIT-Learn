---
name: formula-analysis
description: Analyse a formula symbol by symbol - meaning, assumptions, derivation, interpretation, limiting cases, failure modes, checks - and write a formula note. Activate when the user asks "what does this formula mean", "derive/interpret this", or when a concept note introduces a formula that has no formula note.
---

# formula-analysis

Capability skill. Called by `/study` and `concept-builder`. General rules: `.Codex/rules/` (especially `math-uncertainty.md`).

## Purpose
Turn a formula into understanding: what each symbol is, what must hold, where it comes from, how it behaves, when it breaks.

## Activate when
A formula must be understood, derived, or reused. Prefer the user's source version of the formula; if there is none, say the version is `generated`.

## Inputs
The formula (text, LaTeX, or image via `course-ingestion`), its context/source, and the concept it belongs to.

## Outputs
A `formula` note (template `formula.md`) `FRM-<slug>.md` in `20-Concepts/formulas/`; optional `derivation` note in `30-Derivations/`; recall questions handed to `exercise-generator`.

## Vault interaction
Reads the source record/concept; writes the formula note and links it from the concept. Existing formula notes are extended, not duplicated.

## Skill-specific integrity
- Every symbol is defined with its domain and whether it is random or fixed. Undefined symbols in a source are flagged, not guessed.
- State which checks were done and how: analytic, dimensional, limiting case, or remote numeric run. Never claim a numeric check that was not run.
- If a derivation step is missing or your bridge differs from the source, follow `math-uncertainty.md`.

## Procedure
1. Fix the exact statement and its source.
2. Fill the symbols table and assumptions.
3. Derive (or link to the derivation), justifying each step.
4. Interpret terms; examine limits and edge cases; state failure modes.
5. Run and record checks; add recall links; set status.
