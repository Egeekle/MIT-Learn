# MIT Learning OS

A personal, Markdown-first learning system for the **MIT MicroMasters in Statistics and Data Science**. It combines course material, class notes, PDFs, handwritten-note photos, exercises, papers, derivations, experiments, datasets and projects with error tracking, spaced review and knowledge diagnostics.

- **Obsidian** is the knowledge interface and canonical knowledge base (open this folder as a vault).
- **Claude Code** is the learning agent and system maintainer (run it from this folder).
- **Remote compute:** Python/R run on a remote machine, not locally. See `00-System/Compute.md`. The target is not bound yet.

The point is active learning (recall, derivation, problem solving, experiments, error analysis), not passive note-taking.

## Start here

1. Open this folder in Obsidian (*Open folder as vault*).
2. Start Claude Code in this folder. It reads `CLAUDE.md` and `00-System/memory.md` automatically.
3. Drop material in `01-Inbox/` and run `/ingest`, or run `/study <topic>`.

## Modes

| Command | What it does |
|---|---|
| `/study` | Active-recall session on a concept or unit |
| `/exercise` | Generate and grade problems; log errors |
| `/research` | Find and read papers connected to a concept (citations verified, never invented) |
| `/ingest` | Turn PDFs, photos, notes into provenance-recorded drafts |
| `/diagnose` | Find knowledge gaps from your error history |
| `/project` | Design and run applied experiments remotely |
| `/review` | Spaced-review session |
| `/evolve` | Change the system through the approval gate |

More modes can be added as skill folders without redesign (`00-System/Architecture.md` §5).

## Layout

`00-System/` holds the design (Architecture, Conventions, Compute, Change-Log, memory, Templates). Numbered folders `01`–`99` hold the knowledge; `.claude/` holds agent rules and skills. Full map: `00-System/Architecture.md`.

## Rules you can rely on

- Nothing is fabricated: papers, citations, URLs, datasets and course material are real or marked `UNVERIFIED`. Sources are labelled `mit`, `primary-research`, `secondary`, `generated` or `user`.
- Missing or unclear math in your notes is flagged, never silently filled in.
- Notes move `draft → review → approved`. Only you approve. Approved notes are archived in `99-Archive/versions/` before any change.
- Structural changes are proposed first and made only after you approve; they are recorded in `00-System/Change-Log.md`.
- **The GitHub remote is public and holds only the system architecture** (CLAUDE.md, README, `.claude/`, `00-System/`, empty folder skeleton). PDFs, resources and your notes stay on your computer; nothing is committed or pushed without your say-so.

## Status

Foundation version 0.1.0. No course content ingested yet; the 18.6501x course link is recorded in `00-System/memory.md` but its unit structure is unverified until ingested.
