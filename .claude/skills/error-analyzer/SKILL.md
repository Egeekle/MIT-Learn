---
name: error-analyzer
description: Classify a learner mistake (from an attempt, tutoring session, review or experiment), find its root cause, write an error entry linked to the concept, and define a prevention step. Activate when the user makes or reports a mistake, after grading an attempt, or when a review is missed.
---

# error-analyzer

Capability skill. Called by `/exercise`, `/study`, `/review`. Taxonomy and formats: `00-System/Conventions.md` (Error tracking).

## Purpose
Turn each mistake into a specific, retrievable learning fact: what went wrong, why, and how to prevent it.

## Activate when
A real mistake is observed or the user reports one. Do not create error entries for hypothetical mistakes, except clearly marked fixtures for testing.

## Inputs
The attempt/session/review that shows the mistake; the correct reasoning; the related concept.

## Outputs
One `error-entry` (`ERR-YYYY-MM-DD-<slug>.md`) in `80-Learning/Errors/`: type, concept link, what was done, what was right, root cause, fix, prevention. Optional `review-card` for the prevention step.

## Vault interaction
Reads attempts/sessions and concept notes; writes error entries; updates `status` (open → understood → resolved) when the user shows the fix works. Looks for an existing entry with the same root cause and links it instead of duplicating.

## Skill-specific integrity
- Root causes are hypotheses unless the user confirms them; say so.
- Quote the user's actual work; do not paraphrase it into something more wrong or more right.
- Fixture entries carry `fixture: true` and are labelled synthetic in the body.

## Procedure
1. Locate the exact step where reasoning diverged.
2. Classify with the taxonomy; check for a recurring root cause.
3. Write the entry; link the concept; propose prevention (check-step or review-card).
4. Hand recurring or high-impact patterns to `diagnostic`.
