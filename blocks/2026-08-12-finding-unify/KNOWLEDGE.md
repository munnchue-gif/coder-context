# KNOWLEDGE — Finding unification

## Live shape (authoritative)
```python
# fabric/types.py
@dataclass
class Finding:
    id: str
    organ: str
    severity: str  # 'info', 'warn', 'error', 'critical'
    title: str
    detail: str
    timestamp: float = ...
    metadata: Dict[str, Any] = ...

def make_finding(*, id=..., organ=..., severity=..., title=..., detail=...,
                 section_id=None, kind=None, **_extra) -> Finding:
    # maps old section_id/kind/int severity → live fields
```

## Known hot spots from earlier inspection
- `forge/fabric/bind/ollama_capsule.py` — still constructs with section_id / kind / int severity
- `forge/fabric/bind/openvino_seat.py` — same pattern
- Any remaining imports of Finding from overseer instead of fabric.types

## Discarded material
Any previous incomplete Finding redesigns are discarded. Use the live types.py as the single source of truth.
