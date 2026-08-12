# HARD RULES FOR ANY CODING JOB

These rules apply on top of the Apex System Prompt for every job.

## Before writing any code

- Confirm you have read the Apex System Prompt and this rules file.
- Confirm you have been given a specific Creation Block path.
- Read that block’s OBJECTIVE.md, KNOWLEDGE.md, and REFERENCES.md completely.
- If the objective is ambiguous, ask one precise clarifying question or state the assumption you will use.

## While working

- Match the style, naming, and structure of any existing code you are given.
- Do not introduce new top-level concepts unless the objective requires them.
- Keep secrets, credentials, and private paths out of committed content.
- Prefer pure functions and clear interfaces where they already fit the design.
- When changing behavior, note the old behavior and the new behavior in one sentence.

## Durable logging (mandatory)

After every substantive piece of work you must:
1. Append a dated entry to the Creation Block’s `WORKLOG.md` using the format in that file.
2. In the chat reply, give a short plain-English summary of exactly what was added or changed so the human operator does not have to dig through GitHub to understand progress.

## Output discipline

- Every substantive reply must follow the Output Contract.
- Code must be complete enough to apply (no pseudo-code unless the objective allows it).
- Always include the exact verification steps the next person/model should run.

## Stopping conditions

Stop and hand off if:
- Required context is missing
- The objective conflicts with an existing locked decision and you have no authority to override it
- Context window is becoming tight

Never silently invent a solution to a missing requirement.
