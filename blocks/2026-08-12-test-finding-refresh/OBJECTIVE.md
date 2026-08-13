# OBJECTIVE

## HARD LAYOUT RULE
- Work only in this Creation Block.
- Append to WORKLOG.md only; never edit OBJECTIVE / KNOWLEDGE / REFERENCES.
- Write code only into `the-forge` at the paths named below.
- Do not invent new modules or types.
- Ignore blacklisted repos.

## Job Title
Refresh all remaining Finding-related tests to the live shape

## Goal
Modernize every test file that still constructs or asserts on the dead Finding shape so the entire design suite uses `fabric.types.Finding` + `make_finding` exclusively.

## Target paths in the-forge
- forge/fabric/test_sandbox.py
- forge/fabric/test_conduit.py
- forge/fabric/test_overseer.py
- Any other `forge/fabric/test_*.py` that still contains:
  - `from fabric.overseer import Finding`
  - `Finding(section_id=...`
  - `kind=`
  - `.kind` or `.section_id` on a Finding object

(Do the three named files first. Only touch additional test files if the grep still shows dead Finding usage after those three.)

## Constraints
- Keep every existing test name and the behavioural intent of each test.
- Replace `from fabric.overseer import Finding` (or combined imports) with `from fabric.types import Finding, make_finding`.
- Construct Findings only via `make_finding(...)` using live fields: `id`, `organ`, `severity` (str), `title`, `detail`.
- Replace assertions on `.kind` → `.title`, on `.section_id` → `.id`.
- Severity is a string. Do not compare with `< 3` or `>= 3` on the attribute itself; use a small rank helper or string membership if needed.
- Do **not** change any production module (overseer, sandbox, judge, conduit, etc.).
- Capability `.kind` and ledger event `"kind"` keys are **not** Finding fields — leave those alone.

## Out of scope
- Production code
- test_judge.py (already modernized)
- Removing legacy kwargs from make_finding
- Blacklisted repos

## Success criteria
```bash
grep -n "from fabric.overseer import Finding\|Finding(section_id=\|kind=\|".kind\"\|\.section_id" \
  forge/fabric/test_sandbox.py forge/fabric/test_conduit.py forge/fabric/test_overseer.py
# expected: zero matches related to Finding

python3 -m pytest forge/fabric/test_sandbox.py forge/fabric/test_conduit.py forge/fabric/test_overseer.py -q
# expected: all pass
```

## Deliverables
- Complete updated content for each touched test file
- Short human summary
- One WORKLOG entry
