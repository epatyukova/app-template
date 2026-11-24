# Lightweight architecture checklist

Use this reference for a new system or a change with substantial architectural impact. Start with a one-page description and expand only where risk, complexity, or stakeholder needs justify it. Remove irrelevant prompts rather than leaving empty sections.

This checklist is informed by the concerns organized in [arc42](https://arc42.org/overview/) and its iterative, quality-driven [architecture method](https://arc42.org/method/). Consult the canonical arc42 material when a project needs the complete method or template.

## Outcomes and quality goals

- State the business or user outcome, scope, and explicit non-goals.
- Identify the three most important quality goals before selecting a solution.
- Turn critical qualities into measurable scenarios:
  - trigger or stimulus;
  - relevant operating condition;
  - expected system response;
  - measurable threshold or success criterion.

Example shape: “During normal operation, when an authenticated user requests a common resource, 95% of responses complete within 300 ms.” Use project evidence to choose real thresholds; do not invent them silently.

## Constraints and system context

- Separate hard constraints from assumptions and preferences.
- Identify users, external systems, trust boundaries, and owned versus external responsibilities.
- Describe important interfaces, protocols, data exchanged, and failure expectations.

## Strategy and alternatives

- Summarize the few core ideas that shape the solution.
- Compare credible alternatives when the choice is consequential.
- Explain why the recommendation best satisfies the quality goals and constraints.
- Capture durable decisions as ADRs rather than hiding them in prose.

## Structural view

- Name the major components and give each one a clear responsibility.
- Define ownership of behaviour and data.
- Show allowed dependencies and important interfaces.
- Refine only the components whose internals matter to the current decision.

## Runtime view

Describe the scenarios needed to understand system behaviour, especially:

- a representative successful request or workflow;
- asynchronous events or background jobs;
- authentication and authorization paths;
- timeouts, retries, partial failure, and recovery;
- concurrency or ordering when correctness depends on it.

Use sequence or flow diagrams only where they communicate these interactions better than prose.

## Deployment and operations

When an execution environment exists, describe:

- processes, containers, hosts, managed services, and network boundaries;
- configuration and secret delivery;
- scaling, availability, health, and readiness behaviour;
- logging, metrics, tracing, alerting, backup, and recovery;
- deployment, migration, rollback, and compatibility requirements.

Do not invent a deployment view for an application whose runtime has not been chosen.

## Cross-cutting concepts

Document policies that affect several components only when relevant:

- identity, authorization, security, and privacy;
- validation, error handling, idempotency, retries, and timeouts;
- persistence, transactions, migrations, caching, and consistency;
- configuration, feature flags, dependency boundaries, and versioning;
- observability, testing, build, release, and operational conventions.

Keep enforceable conventions in code, tests, linters, or CI where possible; architecture documentation should explain the intent and boundaries rather than duplicate tool configuration.

## Risks, debt, and vocabulary

- Record known risks, uncertainty, deliberate shortcuts, and technical debt with an owner or follow-up condition where possible.
- Define domain or technical terms only when readers could reasonably interpret them differently.
- Periodically verify that quality goals, decisions, and risks still reflect the implemented and operated system.

## Artifact boundaries

- Active plan: target state, acceptance criteria, implementation order, and rollout.
- Architecture document: durable current state and important system views.
- ADR: one consequential decision, its context, and consequences.
- Code, tests, and deployment configuration: executable evidence of the architecture.
