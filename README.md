# coder-context

**Universal apex context kit + labeled Creation Blocks for coding models.**

## Core idea

- One universal apex prompt set
- Every coding job lives in its own **Creation Block** under `blocks/`
- Each block carries a **fresh, minimal knowledge base** for that job only
- No leftover knowledge from previous jobs or rejected work
- Prefer “create the correct finished files” over “fix the old broken ones”
- Models may append to the current block’s WORKLOG and add deliverables; they must never alter block structure or history

## Layout

```
coder-context/
├── prompts/                 ← universal OS (read every time)
├── blocks/
│   ├── _TEMPLATE/           ← copy for each new job
│   └── YYYY-MM-DD-name/     ← one job, fresh knowledge only
│       ├── OBJECTIVE.md
│       ├── KNOWLEDGE.md     ← only what THIS job needs
│       ├── REFERENCES.md
│       ├── WORKLOG.md       ← append-only
│       └── deliverables/    ← optional
└── archive/                 ← human-managed only (optional)
```

## Rules

- One job = one block
- Knowledge in a block is only for that job
- Rejected or obsolete material is not kept in active blocks
- Models never edit OBJECTIVE / KNOWLEDGE / REFERENCES or other blocks
- Completed blocks stay as history; humans may off-load later

## Starting a new job

1. Copy `blocks/_TEMPLATE/` to `blocks/YYYY-MM-DD-short-name/`
2. Write a fresh OBJECTIVE + KNOWLEDGE that contain only what the job needs
3. Point the model at that block
4. Prefer create-the-correct-files framing over fix-the-old-files framing
