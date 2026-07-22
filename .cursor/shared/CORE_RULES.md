# CORE_RULES.md — Shared policy for all pipeline agents

## Package manager

- Use **npm** only (`npm run build`, `npm test`, `npm run lint`). Do not introduce yarn/pnpm unless the project already does.

## HANDOFF.md

- Append-only.
- After finishing work: short timestamped note with what was done and key decisions.
- Length-aware reading: if > ~150–200 lines, read only the last 30–40 lines + key decisions.

## AGENT_RESULT

- Final message **must** contain `## AGENT_RESULT` (prefer YAML fence).
- Required fields depend on the role; always include `status` and a short Russian or English `summary`.
- Optional: `tokens_used`, `grilled`, `skip_human_approval_recommended`, `verdict`, `exit_checks_passed`, `blockers`.

## Conciseness

- Maximum focus on tagged tasks only.
- Do not re-explain previous steps or full design.
- No scope creep.

## Guardrails

- Never weaken tests to make them pass.
- Never implement production code outside your agent scope.
- Prefer blocking with clear reason over inventing behavior.
- Respect OpenSpec artifacts as source of truth.
