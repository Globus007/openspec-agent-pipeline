# TASK_BATCH_RULES.md (summary)

Used by task-runner for auto-approve decisions.

All conditions must pass for auto-approve:

- Post-propose / spec_review is APPROVED or skipped
- No `[BLOCKER]` in APPROVAL_BRIEF
- Task not marked complex / requires human
- Footprint ≤ ~20 files
- No prior failed/blocked for this change in the batch
- `last_verdict != CHANGES_REQUIRED`
- No blacklisted paths: `lib/calculation/`, `lib/auth/`, `supabase/`, pricing/money/PDF scope

If any fails → fall back to human gate.
