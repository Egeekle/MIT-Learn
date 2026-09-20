---
name: vault-architect
description: Guard the vault's structure and integrity - run the architecture gate for structural changes, keep Architecture/Change-Log/skills/templates consistent, and run the validation checklist. Activate when the user asks to change structure, add a mode/skill/template, bind compute, or asks "is the vault consistent"; also as pre/post-flight around other structural work.
---

# vault-architect

Capability skill. Called by `/evolve`. The gate procedure itself lives in `00-System/Architecture.md` §7 and `.claude/rules/architecture-gate.md`; this skill applies it and does not restate it.

## Purpose
Keep the system modular, evolvable and self-consistent; no silent structural change.

## Activate when
Any structural change is proposed or discovered (folders, schema, templates, modes/skills, rules, compute binding, repo scope), or a consistency check is requested.

## Inputs
The proposed change or the check requested; current `Architecture.md`, `Conventions.md`, `Change-Log.md`.

## Outputs
- A proposal (before approval) covering affected modules and migration.
- After approval: updated Architecture, Change-Log, skills/templates, and `CLAUDE.md` only if persistent behavior changed.
- A validation report.

## Vault interaction
Reads everything under `00-System/`, `.claude/`, and the folder tree. Writes only system files, and only after approval. Does not edit knowledge notes.

## Skill-specific integrity
- Classify every change as major (gate) or not; when unsure, treat it as major.
- Registries stay single-sourced: modes in Architecture §5, capability skills in §5a, templates in the template table. Add a row, do not copy text elsewhere.
- Never rename or move existing notes without a migration entry in the Change-Log.

## Validation checklist
1. Every path named in Architecture exists; every relative link/wikilink resolves (`[[Note]]` in Conventions is a literal example).
2. Every registered mode and capability skill has `SKILL.md` with `name` = folder and an activation-stating description.
3. Every template's frontmatter `type` is in Conventions; every Conventions type has a template.
4. Skills do not restate `CLAUDE.md` or rule text.
5. `git add -n .` lists only architecture files and `.gitkeep`; no notes, fixtures, or sources.
6. `fixture: true` notes are listed, with a cleanup command offered (never run unasked).
