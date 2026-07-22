# AGENT_RESULT contract

Every subagent **must** end with:

```markdown
## AGENT_RESULT

```yaml
status: success | failed | blocked
summary: "1–3 sentences (preferably Russian for user-facing notes)"
exit_checks_passed: true | false   # when applicable
verdict: APPROVED | CHANGES_REQUIRED  # for review / spec-review
grilled: true | false                 # for spec-author
skip_human_approval_recommended: true | false
# tokens_used: { prompt: N, completion: N, total: N }  # optional
# blockers: ["..."]
# review_path: "openspec/changes/.../reviews/review-001.md"
```
```

Orchestrator parses **only** this block for state transitions.
