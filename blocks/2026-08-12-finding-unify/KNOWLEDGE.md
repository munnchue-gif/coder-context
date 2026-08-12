# KNOWLEDGE — fresh for this job only

## Live Finding shape (fabric/types.py)

```python
@dataclass
class Finding:
    id: str
    organ: str
    severity: str   # 'info' | 'warn' | 'error' | 'critical'
    title: str
    detail: str
    ...

def make_finding(*, id=..., organ=..., severity=..., title=..., detail=...,
                 section_id=None, kind=None, **_extra) -> Finding: ...
```

- section_id maps to id
- kind maps to title (and organ if still default)
- int severity maps to string labels

## Import rule
```python
from fabric.types import Finding, make_finding
```

## What this job does NOT need
- No ledger/kernel history
- No rejected zips or parallel finding.py designs
- No UI / spine / arena repos
