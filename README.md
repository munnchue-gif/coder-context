# coder-context

**Universal apex context kit for coding models.**

This repository is the public face any coding model should absorb *before* receiving a specific job.
It is deliberately project-agnostic so the same kit can be reused for different coding jobs without drift.

## Purpose

- Give any coding model a strong, consistent operating system
- Prevent architecture invention and random redesigns
- Provide a clean place to inject job-specific objectives
- Act as the stable public surface even when private project details live elsewhere

## How to use with a coding model

1. Point the model at this repository first (or paste the contents of `prompts/`).
2. Have it read, in order:
   - `prompts/00_APEX_SYSTEM.md` (the universal master prompt)
   - `prompts/01_RULES.md`
   - `prompts/02_OUTPUT_CONTRACT.md`
3. Then give the model a **Job Objective** message (use the template in `jobs/JOB_TEMPLATE.md`).
4. The model executes only the objective while staying inside the apex rules.

## Structure

```
coder-context/
├─ README.md
├─ prompts/
│   ├─ 00_APEX_SYSTEM.md      ← universal apex system prompt
│   ├─ 01_RULES.md            ← hard behavioral rules
│   ├─ 02_OUTPUT_CONTRACT.md  ← how every reply must look
│   └─ 03_HANDOFF.md          ← how to leave clean state for the next model
├─ jobs/
│   ├─ JOB_TEMPLATE.md        ← fill this for each new coding job
│   └─ examples/              ← optional example objectives
└─ reference/
    └─ (optional pointers to real project sources of truth)
```

## Design principles baked in

- Prefer existing architecture over reinvention
- Small, verifiable patches over large rewrites
- Explicit assumptions; never invent missing context
- Clean handoff when context is running low
- Zero sycophancy, maximum precision

This kit is the public operating system.  
Private project details and secrets stay out of it.
