# OBJECTIVE

## HARD LAYOUT RULE
- Work only in this Creation Block.
- You may append to WORKLOG.md and add files under deliverables/ if asked.
- Never edit OBJECTIVE.md, KNOWLEDGE.md, REFERENCES.md, or any other block.
- Never invent new modules (especially no new finding.py).

## Job Title
Create clean Finding construction in the living fabric modules

## Goal
Produce the correct, complete versions of the modules that currently construct Findings, so every Finding is built through the live shape (or make_finding) and uses the live field names.

Target files in the living repo (https://github.com/munnchue-gif/the-forge):
- forge/fabric/bind/ollama_capsule.py
- forge/fabric/bind/openvino_seat.py
- forge/fabric/conduit.py
- forge/fabric/judge.py

(Tests can be handled in a later pass once production files are correct.)

## What “correct” means
- Import Finding and make_finding from fabric.types only
- Construct Findings only via make_finding(...) or the live Finding dataclass
- Use live field names: id, organ, severity (str), title, detail
- Do not create any new Finding module
- Do not change ledger.py or kernel.py

## Constraints
- Prefer the existing structure of each file; only change what is required for correct Finding construction and field access
- Keep behavior the same; this is a shape/construction cleanup, not a redesign
- One file (or one small group) at a time if the operator asks

## Out of scope
- Creating finding.py or any second Finding type
- Rewriting judge/conduit into a new architecture
- Touching ledger, kernel, or other Creation Blocks
- Next.js / unrelated starter files

## Success criteria
- Delivered files import from fabric.types and construct Findings correctly
- No section_id= / kind= / int-severity constructors remain in those files
- No .section_id / .kind field reads remain on Finding objects in those files
- Short verification commands provided

## Deliverables
- Complete file content for the requested module(s)
- One plain-English summary of what changed
- Append one entry to this block’s WORKLOG.md
