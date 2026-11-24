---
name: project-planning
description: Plan a new Python project, substantial feature, or cross-cutting architecture change before implementation. Use when defining scope, system boundaries, data flow, major dependencies, acceptance criteria, or an execution plan; skip for small isolated fixes.
---

# Project Planning

Use this workflow before implementing a new application, service, major feature, integration, data model, or change that affects several parts of the system.

## Planning boundaries

- Inspect the existing repository and current documentation before proposing a design.
- Separate confirmed requirements, assumptions, constraints, and unresolved decisions.
- Do not invent frameworks, services, or operational complexity without a concrete need.
- Compare credible alternatives when a choice has meaningful consequences; recommend one and explain the tradeoff.
- Ask the user only when a missing decision would materially change the product, architecture, data model, security posture, or irreversible work.
- Planning does not authorize deployment, external writes, purchases, or other actions outside the user's request.

## Choose the documentation depth

Start with the smallest architecture description that supports a sound decision. A routine feature may need only goals, affected boundaries, one runtime flow, and risks. For a new system or a change with broad architectural impact, read `references/architecture-checklist.md` and cover the relevant views. Do not create empty sections merely to satisfy a template.

## Define the architecture

Identify the most important quality goals before choosing technologies or components. Express critical qualities as observable scenarios: the triggering condition, operating context, expected response, and measurable threshold.

Cover the dimensions that matter for this project:

- product goal, primary users, scope, and non-goals;
- hard constraints and system context, including external interfaces;
- solution strategy, credible alternatives, and the reason for the recommendation;
- component responsibilities, ownership, and boundaries;
- important runtime scenarios such as requests, events, jobs, and failure paths;
- interfaces, data ownership, persistence, and migration concerns;
- deployment and operational topology when known;
- cross-cutting concepts such as configuration, security, privacy, errors, validation, observability, and dependency management;
- measurable performance, reliability, compatibility, and maintainability requirements;
- testing strategy and acceptance criteria.

Use a small diagram when it makes component or data-flow relationships clearer than prose.

## Produce an execution plan

Create `tasks/active/<short-topic>.md` using `assets/plan-template.md`. Make the plan executable by another agent:

- break work into ordered, independently verifiable steps;
- identify likely files or areas without inventing paths that do not exist yet;
- give each step a concrete outcome and verification method;
- identify risks, rollout or migration needs, and explicit non-goals;
- keep unresolved product choices visible rather than burying them in implementation tasks.

Update `docs/architecture.md` only with durable current-state architecture. Create a short ADR under `docs/decisions/` for a consequential decision that future contributors may otherwise revisit. Do not copy the entire implementation plan into the architecture document.

## Handoff

Present the recommendation, material tradeoffs, and unresolved decisions. If the user already requested implementation and no material decision remains, save the plan and continue; otherwise stop at the decision that needs user direction.

During and after implementation, compare the code and deployment configuration with the plan. Keep the active plan current when implementation materially diverges, update `docs/architecture.md` to reflect the implemented system, and record newly consequential decisions or technical debt rather than leaving target-state documentation that no longer matches reality.
