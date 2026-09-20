---
name: diagnostic
description: Aggregate error entries, attempts, sessions and review history into a ranked, evidence-based diagnosis of knowledge gaps with a targeted practice plan. Activate when the user asks "where am I weak", after a batch of errors, at the end of a unit, or when reviews keep failing. Reports insufficient data instead of guessing.
---

# diagnostic

Capability skill. Called by `/diagnose`. General rules: `.claude/rules/`; taxonomy: `00-System/Conventions.md`.

## Purpose
Find the small number of gaps that explain most errors, and say how to test and repair them.

## Activate when
Enough real evidence exists (guide: at least ~5 non-fixture error entries or attempts touching the target). With less, report "insufficient real data", list what to collect, and stop.

## Inputs
Optional concept/unit/time window. Reads `80-Learning/Errors/`, `40-Exercises/attempts/`, `80-Learning/Reviews/`, prior `80-Learning/Diagnostics/`.

## Outputs
A `diagnostic-report` in `80-Learning/Diagnostics/`: evidence table, ranked gaps, hypotheses with tests, plan (which mode/skill for each gap). Update `memory.md` with the top open gaps.

## Vault interaction
Read-mostly; writes only the report and the memory pointer. Does not edit errors or notes.

## Skill-specific integrity
- **Exclude `fixture: true` notes** from every count and claim.
- Counts are counts of notes you read; no percentages or trends without enough data; cite the error entries behind each claim.
- Causes are hypotheses with a proposed discriminating test.

## Procedure
1. Gather and filter (drop fixtures); count by concept and error type.
2. Stop with an insufficient-data report if the guide threshold is not met.
3. Cluster, rank, hypothesise, propose tests.
4. Write the report and the plan; update `memory.md`.
