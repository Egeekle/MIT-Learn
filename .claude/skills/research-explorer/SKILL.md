---
name: research-explorer
description: Find and actually read real research papers and secondary sources connected to a concept, and record them as paper notes with verified citations, separating primary research from secondary explanation. Activate when the user asks for papers, history, "how is this used in research", or a concept note needs a primary source.
---

# research-explorer

Capability skill. Called by `/research`. General rules: `.claude/rules/source-integrity.md` applies in full.

## Purpose
Connect concepts to real primary literature and clearly labelled secondary explanations, with citations that can be traced.

## Activate when
A source, paper or research connection is requested or needed. If web retrieval is unavailable, say so and stop; do not cite from memory.

## Inputs
Concept/question; existing notes; optional user-supplied papers or links.

## Outputs
`paper-note` (template `paper-note.md`) in `50-Research/`, with `citation` fields filled only from what was retrieved, or `UNVERIFIED`. Links to concept/formula notes; optional experiment idea for `experiment-manager`.

## Vault interaction
Reads concept notes, existing `50-Research/`; writes paper notes; updates the concept's `sources`/Connections only with verified entries. Checks for an existing note on the same paper first.

## Skill-specific integrity
- A citation is recorded only if the page was retrieved and read in this session, or the user supplied it. Store the URL/DOI exactly as retrieved and the retrieval date.
- Keep `primary-research` and `secondary` separate; state what the paper claims versus your interpretation. Claim results only from the text you read.
- Paywalled/unreadable: record as `UNVERIFIED (not read)`; do not describe its contents.

## Procedure
1. Restate the question; list candidate search terms.
2. Search, open and read sources; keep a retrieval log (URL, date, read fully / abstract only).
3. Classify each source; fill the paper note from the text.
4. Relate to course concepts, limitations, and next steps; report gaps in what could be verified.
