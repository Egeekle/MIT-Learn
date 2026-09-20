---
type: system
status: approved
---

# Change Log

Structural and behavioral changes to the system. Newest first. Note content changes (concepts, exercises, etc.) are not logged here; they live in note version history and git.

Entry format:

```
## <version> (<YYYY-MM-DD>): <title>
- Proposed by / approved by:
- Changed:
- Affected modules:
- Migration:
- Docs/skills/CLAUDE.md updated:
```

## 0.2.0 (2026-09-18): Functional learning layer

- Proposed by / approved by: Claude / the user (plan approved 2026-09-18).
- Changed: Added 10 capability skills (course-ingestion, concept-builder, formula-analysis, exercise-generator, socratic-tutor, research-explorer, error-analyzer, diagnostic, experiment-manager, vault-architect); templates `formula.md`, `question.md`; subfolders `20-Concepts/formulas/`, `40-Exercises/questions/`; `fixture: true` convention; `question:` link on `review-card`. The 7 mode skills (all but `/review`) were trimmed to thin orchestrators that call capability skills.
- Affected modules: skills, templates, Conventions, Architecture (§3, §5a), `.gitignore` (`20-Concepts/**/` skeleton), CLAUDE.md (one line).
- Migration: none (no existing notes).
- Validation: Maximum Likelihood architecture test (15 local-only `fixture: true` notes). Findings fixed as clarifications: naming prefixes for experiments/diagnostics/papers, `awaiting-user` session status, `read_status` field on the paper template.

## 0.1.0 (2026-09-18): Foundation

- Proposed by: Claude (architect), plan approved by the user in the initial session.
- Changed: Created the vault/project skeleton: `CLAUDE.md`, `README.md`, `.gitignore`; `00-System/` (Architecture, Conventions, Compute, Change-Log, memory, Templates); numbered knowledge folders `01`–`99`; `.claude/rules/` (5) and `.claude/skills/` (8 modes).
- Affected modules: all (initial creation).
- Migration: none. Git initialised locally on `main`, tracking `origin/main` (`Egeekle/MIT-Learn`, public); existing `.github/` workflows and `LICENSE` kept. Nothing committed or pushed. Repo scope set at user direction: the public repo holds only the system architecture; PDFs, resources and notes stay local (`.gitignore` ignores content folders except `.gitkeep`).
- Docs/skills/CLAUDE.md updated: all created in this entry.
- Open decisions carried forward: see Architecture §9.
