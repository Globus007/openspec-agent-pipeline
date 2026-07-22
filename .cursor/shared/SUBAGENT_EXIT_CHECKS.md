# SUBAGENT_EXIT_CHECKS.md

Each step that declares `exit_checks` in `pipeline-steps.yaml` must run them and write output to `openspec/changes/<change>/logs/<step-id>.log`.

Common checks:

- `npm run build`
- `npm run lint`
- `npm test`

Rules:

- Orchestrator does **not** run these itself.
- For the `test` step with `expect_test_failure: true`:
  - `exit_checks_passed: true` means the tests failed for the *expected* reason (feature not yet implemented).
  - All-green with no new coverage or a broken harness → `failed`.
- Never weaken tests to make exit checks pass.
