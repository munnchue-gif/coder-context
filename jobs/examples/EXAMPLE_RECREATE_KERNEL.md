# EXAMPLE JOB — Recreate / Align Kernel (illustrative only)

## Job Title
Align or recreate a kernel module to a specified design

## Objective
Produce a clean, complete implementation of the target kernel/ledger/gate behavior described in the provided design notes, matching the locked interface and constraints of the surrounding system. Do not invent a parallel architecture.

## Constraints (locked)
- Prefer the existing public entry points and naming of the living system
- Ledger must be constructed before the gate
- Gate decisions must be recorded
- health() and shutdown() must surface ledger state and verification
- No second Finding type or competing kernel

## Inputs the model may use
- The design decision table provided in the chat
- Any reference files the operator pastes or points to

## Out of scope
- Redesigning the rest of the fabric
- Changing public contracts without explicit approval

## Success criteria
- Code compiles / imports cleanly under the stated package layout
- Boot order and health/shutdown behavior match the design
- Verification steps are provided and pass

## Deliverables
- Complete file contents or unified diffs for the affected modules
- Verification commands

## Notes
This is an example shape only. Real jobs replace the objective and constraints with the actual current need.
