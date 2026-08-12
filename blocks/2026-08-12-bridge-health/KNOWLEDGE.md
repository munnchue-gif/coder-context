# KNOWLEDGE — Bridge health

## Current state
- Bridge lives at forge/bridge/server.py
- It already calls boot_forge() on startup
- /health should report booted, organs, and now real ledger stats

## After the ledger/kernel upgrade
- ledger.size() and ledger.head() are now real methods returning proper values
- health() on the kernel was updated to expose audit_entries and audit_head

## Discarded material
None for this block.
