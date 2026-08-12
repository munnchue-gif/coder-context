# coder-context

**Universal apex context kit + labeled Creation Blocks for coding models.**

This repository is the public operating system and task workspace for coding models.
It is deliberately compartmentalized so every coding job lives in its own labeled block.

## Core idea

- One universal apex prompt set (the operating system)
- Every concrete coding job lives in its own **Creation Block** under `blocks/`
- Each block contains only what that job needs: knowledge, objective, reference notes, and the model’s work log
- Models write their commit-style work log *into the block* so other models (and you) can see progress without hunting through chat history
- Chat gives you the human-readable summary; GitHub holds the durable record
- **Creation Blocks are permanent history.** Models may append to the current block’s WORKLOG and add deliverables, but must never alter or delete past blocks or the block structure itself.

## Layout

```
coder-context/
├── README.md
├── prompts/                     ← universal operating system (read first, every time)
│   ├── 00_APEX_SYSTEM.md
│   ├── 01_RULES.md
│   ├── 02_OUTPUT_CONTRACT.md
│   └── 03_HANDOFF.md
├── blocks/                      ← one folder per coding job (permanent records)
│   ├── _TEMPLATE/               ← copy this to start a new job
│   │   ├── OBJECTIVE.md
│   │   ├── KNOWLEDGE.md
│   │   ├── REFERENCES.md
│   │   └── WORKLOG.md
│   └── YYYY-MM-DD-short-name/   ← real jobs live here forever
│       ├── OBJECTIVE.md
│       ├── KNOWLEDGE.md
│       ├── REFERENCES.md
│       ├── WORKLOG.md           ← model appends here only
│       └── deliverables/        ← optional final files the model produces
└── archive/                     ← optional human-managed offline copies (not required)
```

## How a coding model must work

1. Absorb `prompts/` in order (00 → 03).
2. Open the specific Creation Block it was given.
3. Read that block’s `OBJECTIVE.md` + `KNOWLEDGE.md` + `REFERENCES.md`.
4. Do the work on the *target project code* (e.g. the-forge), not on the blocks themselves.
5. Append a clear entry to that block’s `WORKLOG.md` (and put any final files under `deliverables/` if asked).
6. In chat, give a short human summary of what was added so the operator does not have to dig.

## Rules for Creation Blocks (hard)

- One job = one block. Do not mix jobs.
- Never put private secrets or credentials in a block.
- `WORKLOG.md` is append-only. Models never delete previous entries.
- Models must never edit OBJECTIVE / KNOWLEDGE / REFERENCES of any block.
- Models must never delete, rename, or restructure other blocks.
- Previous completed blocks are historical records and stay read-only.
- If a previous weak sketch exists, it is listed only as “discarded reference” and is not authoritative.

## Starting a new job (for the human)

1. Copy `blocks/_TEMPLATE/` to `blocks/YYYY-MM-DD-short-descriptive-name/`.
2. Fill `OBJECTIVE.md` and `KNOWLEDGE.md`.
3. Point the coding model at the new block path.
4. The model does the rest and writes its log into the block.

## Off-loading old work later

When a block is fully reviewed and no longer needed for active work, a human may optionally copy it to `archive/` or an external backup. Models themselves never perform this cleanup.
