---
type: system
status: review
version: 0.1.0
---

# Compute

Policy: all Python/R execution, notebooks, package environments and heavy workloads run **remotely**. Nothing is installed globally on the user's machine. Claude does not connect to or run anything remotely without the user's approval for that action.

## Target binding (single config point)

```yaml
target:
  name: UNBOUND
  kind: ssh            # ssh | codespaces | notebook-service
  host: null           # ssh alias, once bound
  workdir: null        # e.g. ~/mit-learn on the remote
  candidates:
    - AzureUbuntu      # found in ~/.ssh/config, UNVERIFIED (not connected to)
```

Binding a target is an architecture change (gate, `/evolve`). Changing hosts later edits only this block.

## Environments

- Python: `pyproject.toml` + `uv` lockfile per experiment, created on the remote.
- R: `renv` per experiment, created on the remote.
- Environment definitions (small text files) live next to the experiment in `60-Experiments/<name>/`; the environments themselves do not.

## Sync rules

- Vault → remote: experiment spec, code, env definition.
- Remote → vault: small result artifacts only (metrics, tables as Markdown/CSV under a size limit, figures). Large data and model files stay remote.
- Datasets are described by cards in `65-Datasets/`; provenance and license must be recorded, never guessed.

## Run record

Every remote run is logged in its experiment note: date, target, environment lock hash, command, outcome. See the `experiment` template.
