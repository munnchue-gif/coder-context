# OBJECTIVE

## Job Title
Build the definitive Forge-Spine Kernel + AuditLedger (empty-canvas, high quality)

## Goal
Create the best production-grade implementations of the ledger and kernel that belong in the living the-forge fabric.

You have a clean empty canvas for these modules. Previous incomplete sketches are discarded and are not authoritative.

Target package layout (real system):
- forge/fabric/ledger.py
- forge/fabric/kernel.py
- forge/fabric/gate.py only if a change is required to support the design

## Design intent that must be realized
- AuditLedger is tamper-evident: HMAC-SHA-256 over a deterministic canonical form of each entry, with prev_mac chaining so deletion or reordering breaks verification.
- record(topic, payload) is thread-safe and returns a stable id.
- size() and head() are safe under concurrency.
- verify() returns a clear result (ok + detail).
- Kernel boot constructs the ledger FIRST, before the Gate.
- Gate decisions are recorded; ledger failures never kill Gate decisions.
- health() surfaces ledger size and head.
- shutdown() runs ledger.verify() and surfaces the result.
- Respect FORGE_SECRET / domain-separated keys if the surrounding system uses them.

## Constraints (locked)
- Prefer the living package layout and public entry points of https://github.com/munnchue-gif/the-forge
- No parallel / competing architecture
- No second Finding type
- Ledger before Gate in boot order
- Real cryptographic chaining, not a stub
- Keep boot_forge() / ForgeKernel surface coherent

## Out of scope
- RepoSocket, tool sockets, App changes
- Redesigning the rest of the fabric
- Treating any previous weak sketch as the thing to fix

## Success criteria
- Files are complete and match the package layout of the-forge
- Boot order and ledger integration are correct
- Verification is real (HMAC chain)
- Exact verification commands are provided
- A clear entry is appended to this block’s WORKLOG.md

## Deliverables
- Full contents (or clean diffs) for ledger.py and kernel.py (and gate.py only if changed)
- Short reasoning for major design choices
- Exact verification steps
- Work-log entry in WORKLOG.md
