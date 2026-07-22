# APPROVAL_BRIEF.md format

Orchestrator writes `openspec/changes/<change>/APPROVAL_BRIEF.md` (Russian preferred for the user).

When grilling-done and clean:

```markdown
## Approval Brief (post-grilling, lightweight)

Grilling already done → Domain Context and ADRs checked.
Spec review: APPROVED
Blockers: none

Auto-approve applied (grill-handoff-auto) or ready for `/pipeline approve`.
```

Otherwise full brief with problem/scope/risks/tasks summary and clear call to action.
