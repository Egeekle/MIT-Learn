---
type: system
status: review
version: 0.2.0
updated: 2026-09-18
---

# Architecture: MIT Learning OS

A modular, versioned, Markdown-first learning system for the MIT MicroMasters in Statistics and Data Science. Obsidian is the knowledge interface and canonical knowledge base; Claude Code is the learning agent and system maintainer.

## 1. Principles

1. **Markdown-first, portable.** No proprietary databases. Everything is readable without Obsidian or Claude.
2. **Active over passive.** Every mode produces recall, derivation, problem-solving, implementation or diagnosis, not summaries for their own sake.
3. **Source integrity.** Nothing fabricated; every claim carries a source type. See [[Conventions]].
4. **Human-approved canon.** `draft → review → approved`; only the user approves.
5. **Remote compute.** Python/R run remotely; nothing installed globally on the user's machine. See [[Compute]].
6. **No silent architecture changes.** See the gate in §7.
7. **One home per fact.** No duplication across CLAUDE.md, rules, skills, and this file (§2).

## 2. Layers and single sources of truth

| Concern | Home |
|---|---|
| Persistent agent behavior, hard rules, pointers | `CLAUDE.md` (short) |
| Reusable detailed policies | `.claude/rules/*.md` |
| Per-mode procedures | `.claude/skills/<mode>/SKILL.md` |
| System design, module map, mode registry (this file) | `00-System/Architecture.md` |
| Note format, vocabulary, workflow | `00-System/Conventions.md` |
| Compute target and environment policy | `00-System/Compute.md` |
| Structural history | `00-System/Change-Log.md` |
| Learner state (focus, progress, open questions) | `00-System/memory.md` |
| Note shapes | `00-System/Templates/` |
| Knowledge | numbered vault folders (§3) |

Claude Code's own auto-memory (under `~/.claude/projects/...`) is for agent working preferences only. Learning state lives in `memory.md` so it travels with the vault (tracked in git, hence public: keep it non-sensitive).

## 3. Module map (vault = project root)

```
MIT-Learn/
├─ CLAUDE.md  README.md  .gitignore
├─ .claude/
│  ├─ rules/    source-integrity, canonical-workflow, math-uncertainty, compute, architecture-gate
│  └─ skills/   8 modes + 10 capability skills (§5, §5a)
├─ 00-System/   Architecture, Conventions, Compute, Change-Log, memory, Templates/
├─ 01-Inbox/            staging for unprocessed drops
├─ 02-Sources/          raw material + provenance records (mit, class-notes, pdfs, handwritten)
├─ 10-Courses/18.6501x/ course map and unit notes
├─ 20-Concepts/         canonical atomic concept notes; formulas/ (FRM notes)
├─ 30-Derivations/      step-by-step derivations
├─ 40-Exercises/        generated/, attempts/, questions/ (QST notes)
├─ 50-Research/         paper notes
├─ 60-Experiments/      experiment specs and small results (code runs remotely)
├─ 65-Datasets/         dataset cards (local only; data stays remote)
├─ 70-Projects/         projects
├─ 80-Learning/         Errors/  Reviews/  Diagnostics/
└─ 99-Archive/versions/ previous versions of approved notes
```

| Module | Responsibility | Reads | Writes |
|---|---|---|---|
| Sources | Preserve raw material, record provenance | 01-Inbox | 02-Sources (records), 20/30 drafts |
| Knowledge | Canonical concepts and derivations | Sources, Courses | 20-Concepts, 30-Derivations |
| Practice | Exercises and attempts | Knowledge | 40-Exercises, 80-Learning/Errors |
| Research | Paper notes linked to concepts | Knowledge | 50-Research |
| Computation | Experiments, datasets, projects | Knowledge, Practice | 60, 65, 70 (remote runs) |
| Learning loop | Errors, spaced review, diagnostics | Practice, Knowledge | 80-Learning |
| System | Architecture, conventions, changelog | everything | 00-System, .claude |

**Repo scope.** The public GitHub repo tracks only the system (architecture): `CLAUDE.md`, `README.md`, `.claude/`, `00-System/` and the empty folder skeleton. Folders `01`–`99` are local-only content (PDFs, resources, notes, datasets), enforced by `.gitignore`. See [[Conventions]].

## 4. Data flow

```
01-Inbox ──/ingest──▶ 02-Sources (record) ──▶ 20-Concepts / 30-Derivations (draft)
   ▲                                              │
   │                              /study  /research  /exercise
   │                                              ▼
   │                        40-Exercises ──attempt──▶ 80-Learning/Errors
   │                                                        │
   └── new gaps ◀── /diagnose ◀── 80-Learning ◀── /review ──┘
                                   /project ──▶ 60-Experiments / 65-Datasets / 70-Projects (remote compute)
```

## 5. Mode registry (extension point)

A mode is a skill folder `.claude/skills/<name>/SKILL.md`. Adding a mode = add the folder + one row here. No structural change.

| Command | Purpose | Main outputs |
|---|---|---|
| `/study` | Active-recall guided study of a concept/unit; derivation and formula interpretation | session note, concept drafts, review cards |
| `/exercise` | Generate/work problems with hints before solutions | 40-Exercises, attempts, error entries |
| `/research` | Find and read papers connected to a concept; secondary vs primary clearly labelled | 50-Research notes |
| `/ingest` | Process PDFs, photos, class notes into records and drafts, flagging ambiguity | 02-Sources records, drafts |
| `/diagnose` | Analyse errors and recall history for knowledge gaps | 80-Learning/Diagnostics |
| `/project` | Design and run applied projects/experiments on real datasets (remote) | 60/65/70 |
| `/review` | Spaced-review session and queue update | 80-Learning/Reviews |
| `/evolve` | Propose and implement architecture changes through the gate | 00-System, .claude |

## 5a. Capability layer

Modes (§5) are user-facing entry points and stay thin. Capability skills do one job each, auto-trigger from their descriptions, and can be called directly or by modes. Each `SKILL.md` has: Purpose, Activate when, Inputs, Outputs, Vault interaction, Skill-specific integrity, Procedure. General rules stay in `.claude/rules/` and are only referenced.

| Capability skill | Job | Called by | Writes (template → folder) |
|---|---|---|---|
| `course-ingestion` | User material → source records, unit stubs | `/ingest` | source-record → 02-Sources; course-unit → 10-Courses |
| `concept-builder` | Draft/extend concept notes | `/ingest`, `/study` | concept → 20-Concepts |
| `formula-analysis` | Symbol-level formula analysis | `/study`, concept-builder | formula → 20-Concepts/formulas |
| `exercise-generator` | Tiered problems and questions | `/exercise` | exercise → 40-Exercises/generated; question → 40-Exercises/questions |
| `socratic-tutor` | Question-first dialogue | `/study`, `/diagnose` | session → 10-Courses; question; review-card |
| `research-explorer` | Verified papers and sources | `/research` | paper-note → 50-Research |
| `error-analyzer` | Classify and root-cause mistakes | `/exercise`, `/study`, `/review` | error-entry → 80-Learning/Errors |
| `diagnostic` | Evidence-based gap ranking | `/diagnose` | diagnostic-report → 80-Learning/Diagnostics |
| `experiment-manager` | Specify, log, run remote experiments | `/project` | experiment, dataset-card → 60, 65 |
| `vault-architect` | Gate, validation, consistency | `/evolve` | Architecture, Change-Log, system files |

`/review` is self-contained (spaced-review rule lives in its skill). Adding a capability skill = new folder + one row here.

### Template registry

| Concept | Template file (`00-System/Templates/`) |
|---|---|
| Concept | `concept.md` |
| Formula | `formula.md` |
| Exercise | `exercise.md` (+ `exercise-attempt.md`) |
| Question | `question.md` |
| Research Paper | `paper-note.md` |
| Experiment | `experiment.md` (+ `dataset-card.md`) |
| Error | `error-entry.md` |
| Project | `project.md` |
| Review | `review-card.md` |
| Diagnostic | `diagnostic-report.md` |
| Also | `derivation.md`, `source-record.md`, `study-session.md`, `course-unit.md` |

## 6. Note lifecycle

`draft → review → approved`; changes to approved notes are archived per [[Conventions]]. Templates live in `00-System/Templates/`; a template change follows the gate.

## 7. Architecture gate

Before any major structural change (new folder or module, schema change, rename/move of module folders, new mode, compute rebinding, changes to rules or CLAUDE.md behavior):

1. Inspect this file.
2. Propose the change.
3. Explain affected modules.
4. Explain migration requirements.
5. **Wait for approval.**

After approval: implement → update this file → update `Change-Log.md` → update relevant skills → update `CLAUDE.md` if persistent behavior changes.

Not major (no gate): creating notes, exercises, sessions, errors, or dataset cards within existing modules.

## 8. Environment (inspected 2026-09-18)

Local: macOS, git, python3 (pyenv), node, docker, uv, ssh, Obsidian.app. Not installed: R, conda, quarto. No global installs are made for this project. Remote: see [[Compute]].

## 9. Open decisions

| # | Decision | Status |
|---|---|---|
| 1 | Compute target binding (`AzureUbuntu` is an unverified candidate) | open, `/evolve` |
| 2 | Repo visibility (currently public; repo holds architecture only, content is local) | user decision |
| 3 | Optional Obsidian plugins (Dataview, Templater) | open |
| 4 | Whether `.obsidian/` config is tracked | open |
| 5 | Course-specific structure for 18.6501x once unit list is ingested | pending `/ingest` |
| 6 | Backup of local-only content (notes are not in git; versions rely on `99-Archive/`) | open |
