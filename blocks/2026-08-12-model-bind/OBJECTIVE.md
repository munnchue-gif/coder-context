# OBJECTIVE

## Job Title
Bind first real model seat (NPU or Ollama) into the living kernel

## Goal
Make a real model seat (OpenVinoSeat on NPU or OllamaCapsule on RTX) usable by the living ForgeKernel so that `kernel.tick()` can produce findings from a real model instead of only the HeuristicSeat.

The seat must remain observe-only (unconcerned / advisory). It must never act.

## Constraints (locked)
- Use the existing bind scripts/classes in forge/fabric/bind/
- Seat is passed into boot_forge(seat=...) or ForgeKernel(..., seat=...)
- Findings must use the live shape (or make_finding)
- Gate and Overseer separation must stay intact
- No bare model calls outside a sealed section / gate path

## Out of scope
- Building RepoSocket or general tool sockets
- Changing the App
- Full multi-model orchestration

## Success criteria
- A real seat can be constructed and passed to boot_forge
- kernel.tick() returns findings that originate from the real model path
- health / baseline remain green
- Clear verification commands

## Deliverables
- Any needed patches to bind/ or kernel wiring
- Short usage example
- Work-log entry
