# Setup & Import Guide

## 1. Prerequisites

- OpenSpec installed in the target project
- Cursor (or compatible agent host) that can run Task subagents and slash commands
- Matt Pocock skills, at minimum:
  ```bash
  npx skills add mattpocock/skills --skill grill-with-docs
  ```

## 2. Import into a project

**Option A — copy-paste (simplest)**

```bash
git clone https://github.com/Globus007/openspec-agent-pipeline.git /tmp/osp
cp -r /tmp/osp/.cursor your-project/
```

**Option B — git subtree / submodule** (if you want updates)

```bash
git subtree add --prefix .cursor-pipeline https://github.com/Globus007/openspec-agent-pipeline.git main --squash
# then symlink or copy the needed parts
```

## 3. First use

1. Make sure `CONTEXT.md` and (optionally) `docs/adr/` exist.
2. Run `/grill-with-docs` for any non-trivial feature.
3. At the end of grilling append to the change HANDOFF (or create one):

   ```markdown
   ## Handoff from grill-with-docs [YYYY-MM-DD]
   Grilling completed. Domain Context ready.
   ```

4. `/pipeline init <change-name>`
5. `/pipeline` (or `/pipeline run`)

If the handoff marker is present and spec review is clean, the pipeline will auto-approve and proceed to foundation.

## 4. Customization

- Edit `.cursor/shared/pipeline-steps.yaml` for your stack and models.
- Adjust agent scopes in `.cursor/agents/*.md` to match your folder structure (`lib/`, `features/`, `app/`, etc.).
- Expand the short `pipeline.md` with the full original orchestrator logic if you need every edge case (resolveActiveChange, token tables, Russian emitExitRu messages, max_steps, etc.).
