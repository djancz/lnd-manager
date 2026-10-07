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
- Dev server: `.venv/bin/python manage.py runserver 127.0.0.1:8889 --noreload` at `http://127.0.0.1:8889/` <!-- the command stays in the foreground -->

| Check | Command |
|---|---|
| format | `.venv/bin/ruff format --check .` |
| lint | `.venv/bin/ruff check .` |
| typecheck | `.venv/bin/mypy .` |
| test-unit | `.venv/bin/python manage.py test` |
| test-integration | N/A — no separate integration test suite found |
| test-e2e | N/A — no e2e test suite found |
| build | `docker build .` |
| secrets | `gitleaks git --no-banner --redact` |
| deps-audit | `.venv/bin/pip-audit -r requirements.txt` |
| sast | `.venv/bin/ruff check --select S .` |

Project rules (may only tighten the workflow):
- Do not commit `lndg/settings.py`, node credentials, generated data, or workflow records.
- Do not run a Docker build until its external clone and dependency downloads are authorized.
<!-- wf:end -->

— wf-init · 2026-10-07 09:52 UTC
