---
name: experiment-manager
description: Specify, log and (only when a remote target is bound and the user approves) run Python/R experiments and simulations that test a concept, with predictions written before results. Activate when the user wants to simulate, verify numerically, or apply a method to a dataset. Stops after the spec while the compute target is UNBOUND.
---

# experiment-manager

Capability skill. Called by `/project`. Compute policy and target: `00-System/Compute.md`; behavior rules: `.claude/rules/compute.md`.

## Purpose
Make experiments reproducible, honest and linked to theory.

## Activate when
An experiment, simulation or dataset analysis is requested. Check the compute target first.

## Inputs
Question/hypothesis, concept links, optional dataset info (source and license from the user), desired language.

## Outputs
- `experiment` note in `60-Experiments/<name>/` with question, **prediction**, method, environment definition, run log, results, interpretation.
- `dataset-card` in `65-Datasets/` when data is involved; `project` note for multi-experiment efforts.
- Environment definition files (`pyproject.toml` / `renv.lock` specs) are written only when a run is approved.

## Vault interaction
Reads concept/formula notes and `Compute.md`; writes experiment/dataset/project notes; brings back only small artifacts; links misconceptions found to `error-analyzer`.

## Skill-specific integrity
- Write the prediction before any run and keep it unchanged; report agreement or disagreement honestly, including failures.
- Never run or install anything locally. If the target is `UNBOUND`, stop after the spec and say binding requires `/evolve`.
- Datasets: source/license only as provided or verified, else `UNVERIFIED`; no local downloads.
- Record for each run: date, target, environment lock hash, command, outcome.

## Procedure
1. Frame question and prediction; write the spec.
2. Define the environment; check the target; stop if unbound.
3. With approval, run remotely; log the run; sync small results.
4. Compare with the prediction; interpret; hand off errors and follow-ups.
