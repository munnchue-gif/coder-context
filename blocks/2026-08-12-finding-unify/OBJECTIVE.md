# OBJECTIVE

## HARD LAYOUT RULE
- Work only in this Creation Block.
- Append to WORKLOG.md only.
- Write code only into the-forge at the paths below.
- Do not invent finding.py or any second Finding type.
- Ignore blacklisted repos.

## Job Title
Create correct Finding construction in live fabric modules

## Goal
Create the correct, complete versions of the modules that construct Findings so every Finding uses the live shape via make_finding and live field names.

## Target paths in the-forge
- forge/fabric/bind/ollama_capsule.py
- forge/fabric/bind/openvino_seat.py
- forge/fabric/conduit.py
- forge/fabric/judge.py

(Do one file or one small group per request if the operator splits the work.)

## Constraints
- Import only from fabric.types: Finding, make_finding
- Live fields: id, organ, severity (str), title, detail
- Do not change ledger.py or kernel.py
- Keep existing structure; only change what Finding construction requires

## Out of scope
- New modules, other blocks, blacklisted repos, redesign of judge/conduit architecture

## Success criteria
- Delivered files construct Findings only via make_finding / live Finding
- No section_id= / kind= / int-severity constructors left in those files
- No .section_id / .kind reads on Finding objects in those files
- Verification commands provided

## Deliverables
- Complete file content for the requested module(s)
- Short human summary
- One WORKLOG entry
