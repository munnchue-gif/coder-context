# coder-context

**Universal apex operating system + labeled Creation Blocks for coding models.**

## Four active surfaces

| Repo | Permission | Role |
|------|------------|------|
| **coder-context** (this repo) | READ-ONLY for models | Apex prompts + one job at a time |
| **the-forge** | READ/WRITE | Live fabric source of truth |
| **forge-os-core** | READ-ONLY | STATUS.md + LOCKED.md |
| **forge-copilot** | READ/WRITE | Protocol, node logs, handoffs |

All other repos (forge-spine, fabric-core, UI/glass, arena, etc.) are **blacklisted** for core coding jobs.

## Layout

```
coder-context/
├── prompts/
│   ├── 00_APEX_MASTER.md     ← load this first (system OS)
│   ├── 01_RULES.md
│   ├── 02_OUTPUT_CONTRACT.md
│   └── 03_HANDOFF.md
├── blocks/
│   ├── _TEMPLATE/            ← copy for each new job
│   └── YYYY-MM-DD-name/      ← one job, fresh knowledge only
│       ├── OBJECTIVE.md
│       ├── KNOWLEDGE.md
│       ├── REFERENCES.md
│       ├── WORKLOG.md        ← append-only
│       └── deliverables/     ← optional
└── archive/                  ← human-managed only
```

## How a model must work

1. Load `prompts/00_APEX_MASTER.md` (then 01–03).
2. Open **one** Creation Block only.
3. Create correct files in `the-forge` as the block specifies.
4. Append WORKLOG; leave a clean handoff.

## Rules

- Create the correct finished files; do not “fix” rejected work.
- Fresh knowledge only inside each block.
- Never invent parallel modules (e.g. no new finding.py).
- Kernel and Ledger are verified — do not touch unless the block says so.
- Blocks are permanent history; models never delete or rewrite them.

## Starting a new job (human)

1. Copy `blocks/_TEMPLATE/` → `blocks/YYYY-MM-DD-short-name/`
2. Write fresh OBJECTIVE + KNOWLEDGE (only what this job needs)
3. Tell the model: read 00_APEX_MASTER, then BLOCK_OPEN that path
