---
name: fastapi-development
description: Create or modify a FastAPI service when FastAPI is explicitly requested or already present in the Python project.
---

# FastAPI Development

- Do not add FastAPI to the empty template unless the user chooses it.
- Confirm the API boundary, runtime command, configuration, and sync/async requirements before scaffolding.
- Keep request/response schemas explicit and separate transport validation from domain behaviour when useful.
- Use dependency injection for request-scoped resources and lifespan management for shared clients or connection pools.
- Avoid blocking calls on the event loop; use async libraries only when the dependency chain is genuinely asynchronous.
- Convert expected domain failures into deliberate HTTP responses without exposing internals.
- Test routes through an ASGI-compatible client and test domain behaviour below the HTTP layer where appropriate.
- Add health/readiness endpoints only when their semantics and dependencies are defined.
- Run the project quality checks and document the development server command in `README.md`.
