# Compute

Policy and target binding are in `00-System/Compute.md`. Behavioral rules:

- Run Python/R code, notebooks and environment creation only on the bound remote target. Never `pip install`, `brew install`, `install.packages` or create environments on the user's machine.
- Do not connect to a remote host, or start a remote job, without the user's approval for that action. While the target is `UNBOUND`, write experiment specs but do not run them.
- Bring back only small result artifacts. Record every run in the experiment note.
- Never guess dataset sources or licenses; record them from the user or a verified source.
