# OBJECTIVE

## HARD LAYOUT RULE
- Work only in this Creation Block.
- Append to WORKLOG.md only; never edit OBJECTIVE / KNOWLEDGE / REFERENCES.
- Write code only into `the-forge` at the paths named below.
- Do not invent new modules or types.
- Ignore blacklisted repos (spine, fabric-core, UI, arena).

## Job Title
Consumer cleanup — migrate overseer.py feed-log to live Finding fields

## Goal
Update `forge/fabric/overseer.py` so that every place it reads or records a Finding uses the live shape (`id`, `organ`, `severity`, `title`, `detail`) instead of the dead fields (`section_id`, `kind`).

Currently `Overseer.tick()` builds the feed-log with:
```python
"section_id": getattr(f, "section_id", None),
"kind": getattr(f, "kind", None),
```
These attributes no longer exist on live Findings, so the log silently stores `None`.

## Target paths in the-forge
- forge/fabric/overseer.py

## Constraints
- Use live fields only: `id`, `organ`, `severity` (str), `title`, `detail`
- Import Finding from `fabric.types` (already done); do not re-introduce `fabric.overseer.Finding`
- Prefer direct attribute access or a small safe helper; do not invent a second Finding type
- Keep existing structure, methods, and behaviour; change only what is required for live field names
- Do not touch ledger.py, kernel.py, judge.py, conduit.py, or any bind modules

## Out of scope
- test_*.py files (separate future block)
- Removing legacy kwargs from `make_finding`
- Redesign of Overseer / Watcher / Commander architecture
- Other modules, other blocks, blacklisted repos

## Success criteria
- No `section_id` or `kind` reads/writes on Finding objects remain in overseer.py
- Feed-log entries use live keys: at minimum `id`, `title`, `severity`, `detail` (and `organ` if useful)
- Behaviour of tick / drain_findings / stats is unchanged except for correct field names
- Verification grep shows zero legacy field access on Findings

## Deliverables
- Complete updated `forge/fabric/overseer.py`
- Short human summary
- One WORKLOG entry
