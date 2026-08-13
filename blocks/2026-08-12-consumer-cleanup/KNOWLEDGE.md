# KNOWLEDGE — fresh for this job only

## Live interfaces this job must use
- `fabric.types.Finding` shape:
  - `id: str`
  - `organ: str`
  - `severity: str`  # 'info' | 'warn' | 'error' | 'critical'
  - `title: str`
  - `detail: str`
  - (optional) `timestamp`, `metadata`
- Finding is already imported in overseer.py from `fabric.types`

## Import rules
- `from fabric.types import Finding` (already present)
- Package root is `fabric.*` (not `forge.fabric.*`)
- Do **not** import Finding from `fabric.overseer`

## What the current broken code looks like
In `Overseer.tick()`:
```python
self._feed_log.append({
    "section_id": getattr(f, "section_id", None),
    "kind": getattr(f, "kind", None),
    "detail": getattr(f, "detail", None),
    "severity": getattr(f, "severity", None),
})
```
Live Findings have no `.section_id` or `.kind`, so those keys become `None`.

## Correct mapping
| Old (dead)   | Live          |
|--------------|---------------|
| section_id   | id            |
| kind         | title         |
| detail       | detail        |
| severity     | severity      |
| (none)       | organ (useful)|

## What this job does NOT need
- No other Creation Blocks
- No blacklisted repos
- No changes to producers (judge, conduit, bind modules)
- No test file rewrites
- No changes to make_finding signature
