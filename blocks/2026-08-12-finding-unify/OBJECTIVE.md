# OBJECTIVE

## HARD LAYOUT RULE (read first)
- You are working in THIS Creation Block only (`blocks/2026-08-12-finding-unify`).
- You may APPEND to WORKLOG.md and may add files under deliverables/ if requested.
- You must NEVER edit, delete, rename, or move this block’s OBJECTIVE.md, KNOWLEDGE.md, REFERENCES.md, or any other Creation Block.
- The previous ledger/kernel work is COMPLETE and must not be touched by this job.
- Previous blocks are permanent history. Leave them untouched.

## Job Title
Unify all Finding constructors onto the live shape + make_finding

## Goal
Sweep the living fabric so every place that constructs a Finding uses either the live `fabric.types.Finding` shape or the compatibility helper `make_finding`. Remove remaining old-style constructors (`section_id=`, `kind=`, integer severity) so the deferred design-suite tests can be re-enabled cleanly.

## Constraints (locked)
- Live shape is already defined in `fabric/types.py`: id, organ, severity:str, title, detail (+ optional timestamp/metadata)
- `make_finding` already exists and maps old fields → live shape
- Do not invent a second Finding type
- Prefer smallest verifiable patches
- Keep the 62-test baseline green
- Do not modify the already-completed ledger.py or kernel.py

## Out of scope
- Changing the live Finding dataclass itself
- Model binding or bridge changes
- Large refactors unrelated to Finding construction
- Touching any other Creation Block

## Success criteria
- No remaining old-style Finding(...) calls that use section_id / kind / int severity without going through make_finding
- All existing tests that touch Findings still pass
- Clear list of files changed + verification commands

## Deliverables
- Patches or full files for every place that needed updating (in the-forge, not in the blocks)
- Work-log entry in this block’s WORKLOG.md
