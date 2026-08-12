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

## Layout

```
coder-context/
├── README.md
├── prompts/                     ← universal operating system (read first, every time)
│   ├── 00_APEX_SYSTEM.md
│   ├── 01_RULES.md
│   ├── 02_OUTPUT_CONTRACT.md
│   └── 03_HANDOFF.md
├── blocks/                      ← one folder per coding job
│   ├── _TEMPLATE/               ← copy this to start a new job
│   │   ├── OBJECTIVE.md
│   │   ├── KNOWLEDGE.md
│   │   ├── REFERENCES.md
│   │   └── WORKLOG.md
│   └── YYYY-MM-DD-short-name/   ← real jobs go here
│       ├── OBJECTIVE.md
│       ├── KNOWLEDGE.md
│       ├── REFERENCES.md
│       ├── WORKLOG.md           ← model appends here
│       └── deliverables/        ← optional: final files or diffs the model produces
└── archive/                     ← completed or discarded blocks (optional)
```

## How a coding model must work

1. Absorb `prompts/` in order (00 → 03).
2. Open the specific Creation Block it was given.
3. Read that block’s `OBJECTIVE.md` + `KNOWLEDGE.md` + `REFERENCES.md`.
4. Do the work.
5. Append a clear entry to that block’s `WORKLOG.md` (and put any final files under `deliverables/` if asked).
6. In chat, give a short human summary of what was added so the operator does not have to dig.

## Rules for Creation Blocks

- One job = one block. Do not mix jobs.
- Never put private secrets or credentials in a block.
- `WORKLOG.md` is append-only. Models never delete previous entries.
- If a previous weak sketch exists, it is listed only as “discarded reference” and is not authoritative.

## Starting a new job (for the human)

1. Copy `blocks/_TEMPLATE/` to `blocks/YYYY-MM-DD-short-descriptive-name/`.
2. Fill `OBJECTIVE.md` and `KNOWLEDGE.md`.
3. Point the coding model at the new block path.
4. The model does the rest and writes its log into the block.
