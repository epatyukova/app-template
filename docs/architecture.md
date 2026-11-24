# Architecture

## Current state

This is a tooling-first Python project template, not an application architecture. It intentionally defines no package, framework, API, persistence layer, background worker, or deployment target.

## Default shape once implementation begins

Prefer a `src/` layout for packaged code and keep tests outside the package:

```text
src/<package_name>/
tests/
```

Only introduce additional layers when the product requires them. Framework choices, external services, storage, and deployment decisions should be justified by the first concrete use case rather than pre-generated here.

## Boundaries

- Keep domain logic independent from delivery frameworks where that separation has real value.
- Keep configuration explicit and environment-driven; never hard-code credentials.
- Put observable side effects behind small interfaces that are straightforward to test.
- Prefer one canonical tool for each responsibility: uv for environments, Ruff for lint/format, mypy for types, and pytest for tests.

## Architecture documentation once instantiated

Keep this document proportional to the system's risk and complexity. Start with a concise description and expand only the views that help contributors make or verify decisions:

- goals and measurable quality requirements;
- constraints, users, external systems, and trust boundaries;
- solution strategy and major alternatives;
- components, responsibilities, interfaces, and data ownership;
- critical runtime and failure scenarios;
- deployment and operational topology when it exists;
- cross-cutting concepts such as security, configuration, errors, persistence, and observability;
- known risks, deliberate technical debt, and project-specific vocabulary.

The `project-planning` skill contains an arc42-informed lightweight checklist for substantial architecture work. Keep proposed target-state detail in the active plan until it is implemented; this document should describe the durable current state.

## Decisions

Record durable, consequential decisions under `docs/decisions/` using a short ADR containing context, decision, consequences, and status. Do not create ADRs for routine implementation details.
