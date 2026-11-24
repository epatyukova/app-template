---
name: python-containerization
description: Add or update Docker packaging for a Python project once its runtime entry point and deployment requirements are known.
---

# Python Containerization

Do not create a Dockerfile for the empty template. First identify the actual runtime command, network port, required system libraries, and whether the output is an application or library.

When containerization is requested:

- Use a small official Python base image compatible with `requires-python` and pin an appropriate version.
- Install dependencies from the committed lockfile with reproducible settings.
- Copy dependency metadata before source code to preserve build cache reuse.
- Use a non-root runtime user and a minimal writable filesystem surface.
- Add a `.dockerignore` that excludes Git data, virtual environments, caches, tests when appropriate, local metrics, and secrets.
- Never bake `.env` files, credentials, or build-system tokens into an image.
- Add a health check only when the application exposes a real readiness or health mechanism.
- Build the image and exercise its actual startup command before reporting completion.
- Keep deployment-provider configuration separate from the portable image unless the user chooses a provider.
