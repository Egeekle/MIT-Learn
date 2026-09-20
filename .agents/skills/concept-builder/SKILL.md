---
name: concept-builder
description: Build or extend a draft concept note (definition, intuition, assumptions, derivation link, worked example, recall prompts) from sources already in the vault or supplied by the user. Activate when the user asks to "build/write up/create a concept note", after ingestion produces material, or when a study session exposes a missing concept note.
---

# concept-builder

Capability skill. Called by `/ingest` and `/study`. General rules: `.Codex/rules/`; formats and workflow: `00-System/Conventions.md`.

## Purpose
Maintain atomic, linked, source-labelled concept notes that support recall and derivation, not summaries.

## Activate when
A concept lacks a note, or a note needs extension after new material or an error. Search `20-Concepts/` first; extend rather than duplicate.

## Inputs
Concept name; source records/notes to draw from; optional user answers from a tutoring session.

## Outputs
A `concept` note (template `concept.md`) in `20-Concepts/`, status `draft`/`review`, with links to `[[FRM-...]]`, `[[derivation]]`, `[[QST-...]]`, related concepts, and papers. Recall prompts belong in `## Recall` or as `question` notes.

## Vault interaction
Reads `02-Sources/`, `10-Courses/`, `20-Concepts/`, `80-Learning/Errors/` (known misconceptions to address). Writes concept drafts. Editing an `approved` note follows the archive procedure in Conventions.

## Skill-specific integrity
- Label each section's origin (`mit`/`user`/`secondary`/`generated`). Content from general knowledge with no source is `generated`, `sources: UNVERIFIED`, and is never described as course content.
- Put formulas in `formula` notes via `formula-analysis`; keep only the headline form in the concept.
- Include assumptions and failure conditions, not just the definition.

## Procedure
1. Locate existing notes and sources; list what is known vs missing.
2. Draft from the template, section by section, labelling origins.
3. Link formulas/derivations/questions; request them from `formula-analysis` / `exercise-generator` when absent.
4. Mark gaps with `> [!uncertain]`; set `status: review` and list what the user should verify.
