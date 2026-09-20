# Architecture gate

The procedure is defined in `00-System/Architecture.md` §7. Summary of when it applies: new or renamed module folders, schema/template changes, new modes, compute rebinding, and any change to rules, skills' contract, or CLAUDE.md behavior.

- Propose first (inspect Architecture.md, affected modules, migration), then wait for approval. Use `/evolve`.
- After approval: implement, then update Architecture.md, `Change-Log.md`, relevant skills, and CLAUDE.md only if persistent behavior changed.
- Creating notes, exercises, sessions, errors or dataset cards inside existing modules is not a structural change.
