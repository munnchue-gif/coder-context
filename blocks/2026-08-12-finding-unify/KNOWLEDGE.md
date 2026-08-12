# KNOWLEDGE — Finding construction (fresh for this job only)

## Live Finding shape (the only one that exists)

Location: fabric/types.py in the-forge

```python
@dataclass
class Finding:
    id: str
    organ: str
    severity: str   # 'info' | 'warn' | 'error' | 'critical'
    title: str
    detail: str
    timestamp: float = ...
    metadata: dict = ...

def make_finding(
    *,
    id: str = "unknown",
    organ: str = "fabric",
    severity: str | int = "1",
    title: str = "finding",
    detail: str = "",
    section_id: str | None = None,  # mapped to id
    kind: str | None = None,        # mapped to title (and organ if still default)
    **_extra,
) -> Finding:
    ...
```

## Rules for this job
- Always import from fabric.types: `from fabric.types import Finding, make_finding`
- Prefer make_finding(...) when converting old call sites
- Live field names to use when reading a Finding: .id, .organ, .severity, .title, .detail
- Do not invent helpers in a new file; keep changes inside the target module

## Living package layout
- Package import root: fabric.*
- Public entry examples: from fabric.types import Finding, make_finding
- Do not use forge.fabric.* as the import path for these modules

## What this job does NOT need
- No ledger or kernel history
- No rejected zips or parallel finding.py designs
- No Next.js / app starter context
