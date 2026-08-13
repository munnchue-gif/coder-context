# KNOWLEDGE — fresh for this job only

## Live Finding shape (source of truth)
```python
from fabric.types import Finding, make_finding

# Construction
f = make_finding(
    id="section-or-id",
    organ="sandbox",          # or "conduit", "overseer", etc.
    severity="error",         # "info" | "warn" | "error" | "critical"
    title="drift",            # was kind=
    detail="state diverged",
)
```

## Dead → Live mapping
| Old (dead)     | Live              |
|----------------|-------------------|
| section_id=    | id=               |
| kind=          | title=            |
| severity=int   | severity=str      |
| f.kind         | f.title           |
| f.section_id   | f.id              |
| from fabric.overseer import Finding | from fabric.types import Finding, make_finding |

## Severity ranking (if a test needs numeric comparison)
```python
_SEV_RANK = {"info": 1, "warn": 2, "error": 3, "critical": 3}
def _sev_rank(s):
    if isinstance(s, int):
        return max(0, min(3, s))
    return _SEV_RANK.get(str(s), 3)
```

## What is NOT a Finding field (leave these alone)
- Capability `.kind` (e.g. `signed.kind`, `cap.kind`)
- Ledger / event dict keys named `"kind"`
- Bus `section_id` in status dicts

## Already done
- test_judge.py is already on the live shape — do not touch it.
- Production modules (overseer, sandbox, judge, conduit, bind) are already clean.
