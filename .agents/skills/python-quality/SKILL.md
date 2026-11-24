---
name: python-quality
description: Configure, run, or repair Python linting, formatting, type checking, and tests using Ruff, mypy, pytest, and uv.
---

# Python Quality

Use the configuration in `pyproject.toml` as the source of truth.

- Reproduce failures with the narrowest relevant command before changing code or configuration.
- Prefer fixing code over weakening a rule. Add a narrow ignore only when the rule is genuinely inappropriate, and document why.
- Use Ruff for both linting and formatting; do not add overlapping formatters or import sorters without a demonstrated need.
- Keep mypy strict for owned code. Address untyped third-party boundaries locally rather than disabling checks project-wide.
- Keep tests deterministic and independent of production services. Use fixtures at the smallest useful scope.
- Run `uv run ruff check .`, `uv run ruff format --check .`, `uv run mypy .`, and `uv run pytest` when the project contains applicable source and tests.
- Do not claim a check passed when it was skipped or unavailable.
