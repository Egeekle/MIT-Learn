---
name: course-ingestion
description: Turn user-provided course material (PDFs, handwritten-note photos, class notes, MIT Learn pages the user supplies) into provenance-recorded source records and unverified unit stubs. Activate when the user adds or points to material, or asks to "ingest", "add my notes", "process this PDF". Never runs without an actual source.
---

# course-ingestion

Capability skill. Called by `/ingest`; also usable directly. General rules: `.Codex/rules/`; formats: `00-System/Conventions.md`.

## Purpose
Preserve raw material and its provenance, and extract its content faithfully, with every doubt visible.

## Activate when
The user supplies or names a file/text/URL to add to the vault. **Do not activate on a topic name alone**: with no source, say so, ask for material, and create nothing beyond an optional `unverified: true` unit stub.

## Inputs
File paths (in `01-Inbox/` or elsewhere), pasted text, or a URL the user provided. Optional: course, unit, source type.

## Outputs
- `source-record` (`SRC-<slug>.md`) in the matching `02-Sources/` subfolder.
- `course-unit` stub in `10-Courses/<course>/` (status `draft`, `unverified: true` until checked against the course).
- Faithful transcription notes handed to `concept-builder`; never finished canon.

## Vault interaction
Reads `01-Inbox/`, existing `02-Sources/`, `10-Courses/`. Writes source records and unit stubs. Moves originals into `02-Sources/` only after the user confirms; never edits originals. Everything under `02-Sources/` is local-only.

## Skill-specific integrity
- The user's course URL proves nothing about unit structure or content; record units only from ingested material.
- Record each `[?]` token, unreadable region, cut-off page and missing step in the source record's ambiguity lists; do not resolve them.
- No local OCR/conversion installs; read PDFs and images directly, or propose a remote job.

## Procedure
1. Inventory files; check for an existing source record (dedupe).
2. Read and transcribe; mark doubts `[?]`; note page/unit/timestamp locations.
3. Write the source record (completeness: complete / partial / unknown).
4. Write or update the unit stub: scope as observed only.
5. Report what was captured, what is uncertain, and what the user must check against the original.
