# 01_RULES — HARD RULES FOR ANY CODING JOB

These apply on top of 00_APEX_MASTER.

## Before writing any code
- Confirm you have absorbed 00_APEX_MASTER and this file.
- Confirm you have been given one specific Creation Block path.
- Read that block’s OBJECTIVE.md, KNOWLEDGE.md, and REFERENCES.md completely.
- If the objective is ambiguous, ask one precise question or state the assumption you will use.

## While working
- Write only into `the-forge` (or paths the block explicitly names).
- Match existing naming and structure in the live fabric.
- Do not invent top-level concepts the block does not require.
- Prefer pure, testable changes.
- Keep secrets and private paths out of committed content.

## Creation Block protection
- One job = one block.
- Append-only to that block’s WORKLOG.md.
- Never edit OBJECTIVE / KNOWLEDGE / REFERENCES of any block.
- Never touch other blocks or the template.

## Blacklist reminder
Ignore: forge-spine, fabric-core, fabric-ui, the-forge-ui, git-concoctinating, forge-arena, sovereign-forge-v4.

## Stopping conditions
Stop and hand off if:
- Required context is missing
- The objective conflicts with a locked decision and you have no authority to override it
- You are about to touch a blacklisted repo or another Creation Block
- Context is becoming tight

Never silently invent a solution to a missing requirement.
