# OBJECTIVE

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

## Out of scope
- Changing the live Finding dataclass itself
- Model binding or bridge changes
- Large refactors unrelated to Finding construction

## Success criteria
- No remaining old-style Finding(...) calls that use section_id / kind / int severity without going through make_finding
- All existing tests that touch Findings still pass
- Clear list of files changed + verification commands

## Deliverables
- Patches or full files for every place that needed updating
- Work-log entry in this block’s WORKLOG.md
