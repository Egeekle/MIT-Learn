---
name: ingest
description: Ingest PDFs, photos of handwritten notes, class notes or MIT course material into the MIT Learning OS vault with provenance and explicit ambiguity marking. Use for /ingest, "add these notes", "process this PDF/photo".
---

# /ingest

Mode (entry point). Argument: path(s) in `01-Inbox/` or elsewhere, or pasted text.

1. Run `course-ingestion` on the material (source records, unit stubs). No source given: it asks for one and creates nothing.
2. Run `concept-builder` for concepts the material introduces (drafts only).
3. Report to the user: what was created, what is uncertain, what they must check against the originals.
