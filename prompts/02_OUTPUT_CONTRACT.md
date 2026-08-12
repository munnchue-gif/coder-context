# OUTPUT CONTRACT

Every substantive reply from the coding model must use this structure.

```
---
### AI NODE COMMIT LOG
**Model:** [model name or "local"]
**Block:** [path of the Creation Block, e.g. blocks/2026-08-12-kernel-v3]
**Target:** [one clear target for this reply]

#### 1. Reasoning
> Why this approach. What existing pieces were preserved. Any assumptions made.

#### 2. Changes
> Exact file paths and the concrete patches or full file contents.  
> Prefer unified diff style or complete replacement files that can be applied directly.

#### 3. Work Log Written
> Confirm you appended an entry to WORKLOG.md in the Creation Block.  
> Quote the short summary you wrote there.

#### 4. Verification
> Exact commands or checks the next model/human must run.  
> What success looks like. What failure looks like.

#### 5. Handoff (if work remains)
> Remaining steps in order.  
> Anything the next session must know.
---
```

Short clarification questions may omit the full contract.  
Any code, design decision, or status update must use it.
