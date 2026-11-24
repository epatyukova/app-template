# Python Project Template

A small, tooling-first template for Python projects developed with coding agents such as Pi and Cursor.

> **Current state:** this repository intentionally contains no application scaffold. There is no `src/` package, API, CLI, database, or deployment configuration yet. Add only the structure required by the first real use case.

## Included

- `uv` project and dependency management
- Ruff linting and formatting
- mypy strict type checking
- pytest and coverage tooling
- pull-request CI and a PR template
- shared Pi/Cursor agent skills, including project and architecture planning
- optional, privacy-conscious Pi usage metrics
- lightweight architecture, task, and evaluation documentation

## Create a project from this template

1. Copy or generate a repository from the template and initialize Git if necessary.
2. Replace `python-project-template` in `pyproject.toml` with the real distribution name.
3. Choose a package import name, then create `src/<package_name>/` and `tests/` when implementation begins.
4. Update the description, supported Python version, and copyright holder in `LICENSE`.
5. Run `uv lock`, commit `uv.lock`, and verify the quality checks below.

## Local setup

Install [uv](https://docs.astral.sh/uv/), then run:

```bash
uv sync --locked --all-groups
```

The template uses Python 3.13 locally and supports Python 3.12 or newer by default. Change `.python-version`, `requires-python`, Ruff's target, and mypy's Python version together if the project needs a different baseline.

## Quality commands

```bash
uv run ruff check .
uv run ruff format --check .
uv run mypy .
uv run pytest
```

Apply safe Ruff fixes and formatting with:

```bash
uv run ruff check --fix .
uv run ruff format .
```

Until Python source and tests exist, CI reports the type-check and test steps as skipped. Once a scaffold is added, these become normal required checks without changing the workflow.

## Adding an application scaffold

A typical packaged application can start with:

```text
src/<package_name>/
tests/
```

At that point, remove `package = false` from `[tool.uv]`, add a build backend if the project should be packaged, and configure any CLI or server entry points. Do not add FastAPI, Docker, a database, or deployment files until the project actually needs them.

For FastAPI work, containerization, or quality-tool changes, the shared skills under `.agents/skills/` contain the project conventions used by both Pi and Cursor.

## Planning-first workflow

Before starting a new project, substantial feature, integration, data model, or cross-cutting change, use the `project-planning` skill. It produces an active plan under `tasks/active/`, defines quality goals and relevant architecture views, and updates durable architecture documentation or ADRs when appropriate. Its lightweight checklist is informed by [arc42](https://arc42.org/overview/) but tailored to the project's actual risk and complexity. Small local fixes do not require this ceremony.

## Continuous integration

`.github/workflows/ci.yml` runs on pull requests and pushes to the default branch. It:

- installs the locked environment with uv;
- runs Ruff lint and format checks;
- runs mypy when Python source exists; and
- runs pytest when tests exist.

Keep `uv.lock` committed for applications so local development and CI use the same dependency resolution.

## Environment variables and secrets

Copy `.env.example` to `.env` only when local environment variables are needed. `.env` files are ignored; `.env.example` must contain names and safe example values only, never real credentials.

## Agent support

- `AGENTS.md` contains stable project-wide rules and canonical commands.
- `.agents/skills/` contains task-specific guidance shared by Pi and Cursor.
- `.pi/settings.json` contains project-level Pi settings.
- `.pi/extensions/usage-log.ts` writes local metrics to `.pi/metrics/usage.jsonl`.

The metrics extension records model name, token/cost estimates, tool counts, elapsed time, and a generated run ID. It does not record prompts, responses, paths, or tool arguments. Set `PI_EVAL_TASK_ID` to attach a non-secret benchmark task identifier. Metrics are git-ignored.

Human-readable interaction notes are not automatic. If you explicitly want to preserve a session summary, ask the agent to use the `interaction-log` skill; it should redact secrets and write only a concise outcome-oriented note.

## Repository map

```text
.agents/skills/       Shared Pi/Cursor workflows
.github/              Pull-request automation and template
.pi/                  Pi settings and local extension
docs/                 Architecture and decision records
evals/                Optional coding-agent evaluation records
tasks/                Backlog and active implementation plans
```

## License

This template is available under the [MIT License](LICENSE). When creating a project from it, update the copyright holder in `LICENSE`.
