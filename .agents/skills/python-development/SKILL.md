---
name: python-development
description: Implement or modify ordinary Python application and library code while preserving the project's chosen architecture and toolchain.
---

# Python Development

- Read `pyproject.toml`, `AGENTS.md`, and relevant architecture documentation before changing code.
- Confirm whether the project is an application or library before adding packaging, entry points, or deployment assumptions.
- Preserve the package manager and existing source layout. This template has no scaffold until a user requests one.
- Prefer small typed interfaces, explicit dependencies, and standard-library features when they are sufficient.
- Keep configuration outside business logic and never hard-code secrets.
- Add or update focused tests for changed behaviour.
- Run targeted tests first, then the relevant Ruff, mypy, and pytest checks from `AGENTS.md`.
- Report changed behaviour, checks executed, and any remaining limitations.
