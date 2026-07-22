# OpenSpec Agent Pipeline

Reusable **multi-agent OpenSpec pipeline** for Cursor / Claude Code / similar agentic IDEs.

Combines:

- **OpenSpec** (spec-driven development)
- Specialized role agents (foundation → red tests → backend → frontend → QA → review → archive)
- **grill-with-docs** (Matt Pocock skills) for domain modeling *before* writing specs
- Thin orchestrator (`/pipeline`) with disk state, HANDOFF, auto-approve after successful grilling, review cycles, and batch mode

Designed so you can **copy the `.cursor/` folder** (or the whole repo) into any project and start using `/pipeline`.

## Quick Start

1. Install OpenSpec in your project (`openspec init` or follow https://openspec.pro / Fission-AI/OpenSpec).
2. Install Matt Pocock skills, especially:
   ```bash
   npx skills add mattpocock/skills --skill grill-with-docs
   # or the full set
   ```
3. Copy the `.cursor/` directory from this repo into your project root (or merge carefully).
4. (Recommended) Ensure you have:
   - `CONTEXT.md` (glossary)
   - `docs/adr/` for Architectural Decision Records
   - `ARCHITECTURE.md`

### Typical flow

```text
/grill-with-docs          # domain language + ADRs first
# at the end of grilling put a Handoff marker into HANDOFF.md

/pipeline init my-feature
/pipeline run             # or just /pipeline
```

If grilling handoff is present and spec review is clean → **auto-approve** and continue to foundation (no second human gate).

## Structure

```text
.cursor/
├── agents/                 # Role definitions (read by Task subagents)
│   ├── spec-author.md
│   ├── spec-reviewer.md
│   ├── foundation-agent.md
│   ├── test-engineer.md
│   ├── backend-implementer.md
│   ├── frontend-implementer.md
│   ├── qa-verifier.md
│   ├── reviewer.md
│   ├── fixer.md
│   ├── archiver.md
│   ├── task-runner.md
│   └── api-client-agent.md   # optional
├── commands/
│   └── pipeline.md           # /pipeline orchestrator
└── shared/
    ├── CORE_RULES.md
    ├── AGENT_RESULT.md
    ├── SUBAGENT_EXIT_CHECKS.md
    ├── APPROVAL_BRIEF.md
    ├── COMPLETION_SUMMARY.md
    ├── pipeline-steps.yaml
    └── TASK_BATCH_RULES.md
```

## Key ideas

- **Grilling first** → Domain Context section in proposal/design → auto-approve possible
- Strict agent scopes + `<!-- agent:xxx -->` tags in `tasks.md`
- Red tests before implementation
- Independent reviewer + fixer (only BLOCKERs)
- Disk state (`pipeline-state.json`, `HANDOFF.md`) so the orchestrator stays thin
- Safe auto-approve in batch mode (blacklists calc/auth/supabase etc.)

## Customization

- Edit `pipeline-steps.yaml` for step order / models / optional steps
- Adjust agent scopes for your architecture (lib vs features vs app)
- Extend `CORE_RULES.md` with project-specific guardrails

## License

MIT (or change as you like). Use freely in commercial and open-source projects.

---

Inspired by OpenSpec + Matt Pocock's grilling skills + production multi-agent SDLC patterns.
