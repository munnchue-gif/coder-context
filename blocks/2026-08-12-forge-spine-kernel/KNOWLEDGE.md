# KNOWLEDGE — Forge-Spine Kernel job

## Living system (authoritative)

- Public source of truth: https://github.com/munnchue-gif/the-forge
- Package: `fabric.*`
- Public entry: `from fabric.kernel import boot_forge, ForgeKernel`
- Existing organs include ledger, gate, bus, overseer, conduit, wraps, arena, tailor
- Finding shape lives in `fabric.types`
- Bridge boots via `boot_forge()` and must keep working
- Simple baseline of 62 tests must stay green

## Design intent (what we are building toward)

- Strong, tamper-evident AuditLedger (HMAC-SHA-256 + prev_mac chain)
- Thread-safe record / size / head / verify
- Kernel constructs ledger first, wires Gate so decisions are recorded
- health() and shutdown() surface ledger state and verification result
- Clean, production-quality code that fits the living package

## Discarded material (NOT authoritative)

Any previous incomplete or context-free sketches of a simpler Kernel/Gate/Ledger are discarded. Do not treat them as the thing to fix or extend. This is an empty-canvas build of the definitive versions that belong in the living system.
