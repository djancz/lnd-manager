<!-- wf:begin — managed by wf-init; edit the values, keep the markers -->
## Development workflow (wf)

Work records are private in `development/`, shared among this clone's worktrees. New project:
`wf prd` → `wf spec` → `wf roadmap` → `wf milestone`. Each task:
`wf task` → `wf plan` → `wf plan loop` → Gate 1 → `wf wave start` → `wf new-worktree` →
`wf test` → `wf impl` → `wf impl loop` → `wf wave integrate` → Gate 2 → `wf finalize`.
Use `wf status` to resume. `wf maintenance` and `wf deploy` are optional.
If your agent does not load skills, read the matching `wf-<stage>/SKILL.md` under its installed
project directory: `.claude/skills/`, `.agents/skills/`, `.gemini/skills/`, or `.opencode/skills/`.
`wf plan rev` is `wf-plan-review`, `wf impl rev` is `wf-impl-review`, and `wf sec` is
`wf-security-review`.

- Base branch: master
- Max review rounds: 3
- Models: default <!-- default | auto -->
- Test agent: self <!-- self | claude | codex | gemini | opencode -->
- Test model: default
- Test effort: default
- Rev agent: self
- Rev model: default
- Rev effort: default
- Sec agent: self
- Sec model: default
- Sec effort: default
- Fix agent: self
- Fix model: default
- Fix effort: default
- Dev server: none <!-- `<command>` at <url>, for browser checks; the command stays in the foreground -->

| Check | Command |
|---|---|
| format | `ruff format --check --exclude '*_pb2*.py' --exclude gui/migrations .` |
| lint | `ruff check --extend-exclude '*_pb2*.py' --extend-exclude gui/migrations .` |
| typecheck | planned — set up in the first task |
| test-unit | planned — set up in the first task |
| test-integration | N/A — no integration tests |
| test-e2e | N/A — no e2e tests |
| build | N/A — no build step; the Dockerfile clones and builds upstream lndg, not this tree |
| secrets | `gitleaks git --no-banner --redact` |
| deps-audit | `pip-audit -r requirements.txt` |
| sast | `bandit -q -r . -x ./gui/lnd_deps,./gui/migrations` |

Project rules (may only tighten the workflow):
- none yet
<!-- wf:end -->
