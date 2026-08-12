# OBJECTIVE

## Job Title
Prove and harden bridge health path after ledger/kernel upgrade

## Goal
Ensure the FastAPI bridge still boots cleanly with the new ledger + kernel, returns `"booted": true` on /health, and correctly surfaces audit_entries / audit_head from the real ledger.

## Constraints (locked)
- Bridge must continue to use boot_forge()
- Do not re-introduce bare ForgeKernel() construction
- Keep the contract surface stable

## Out of scope
- App UI changes
- New endpoints beyond what the contract already defines

## Success criteria
- `curl http://127.0.0.1:8787/health` returns booted: true and sensible audit fields
- Baseline tests still pass
- Any small bridge patches needed are delivered with verification commands

## Deliverables
- Any required patches to forge/bridge/server.py
- Verification commands
- Work-log entry
