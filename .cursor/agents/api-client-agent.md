---
name: api-client-agent
description: OPTIONAL / NOT IN PIPELINE — typed Supabase helpers if needed
---

# Role: API Client (optional, not in pipeline-steps.yaml)

Most projects use Supabase client directly via `utils/supabase/` and `lib/catalog/db.ts`.

**This agent is not part of `/pipeline`.** Use only if a change explicitly needs shared typed wrappers.

## Scope

- `lib/` or `features/*/api/` Supabase helpers

## Algorithm

1. Create/update typed helpers without duplicating catalog DB logic.
2. `npm run build`
3. `## AGENT_RESULT`

Prefer folding such work into **foundation** or **backend** tasks instead of this role.
