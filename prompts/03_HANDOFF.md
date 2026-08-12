# CLEAN HANDOFF FORMAT

When context is low or a session ends, leave this both in chat and as the latest entry in the Creation Block’s WORKLOG.md:

```markdown
## Handoff

**Block:** [path]
**Status:** [done / partial / blocked]

### Completed
- ...

### Remaining (ordered)
1. ...
2. ...

### Exact next commands
```bash
# paste runnable commands
```

### Critical context the next model must not lose
- ...

### Open questions / blockers
- ...
```

Never leave half-applied changes without a handoff.
