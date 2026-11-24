# <Plan title>

- Status: draft
- Owner: <person or agent>
- Updated: YYYY-MM-DD

## Goal

What outcome should this work produce, and for whom?

## Context

What exists today? List confirmed constraints and relevant evidence.

## Quality goals

List the few qualities that will drive architecture decisions. Give critical goals an observable scenario and measurement.

| Quality | Scenario | Success measure |
|---|---|---|
| <reliability, performance, security, maintainability, etc.> | <trigger, operating condition, expected response> | <measurable threshold> |

## Scope

### In scope

- <required outcome>

### Out of scope

- <deliberately deferred work>

## Assumptions and open decisions

- Assumption: <statement and how it will be validated>
- Decision needed: <choice, recommendation, and consequence>

## Proposed architecture

Complete only the subsections relevant to the work. For a new system or broad architecture change, consult `references/architecture-checklist.md` from the `project-planning` skill.

### Constraints and system context

State hard constraints, users, external systems, trust boundaries, and important interfaces.

### Solution strategy and alternatives

Summarize the recommended approach, credible alternatives, and why the recommendation best satisfies the quality goals.

### Components and ownership

Describe major responsibilities, boundaries, data ownership, and allowed dependencies.

### Critical runtime scenarios

Describe the important successful flow and any asynchronous, failure, recovery, concurrency, or ordering paths that affect the design.

### Data and persistence

Describe important data, ownership, lifecycle, consistency, migration, and privacy concerns, or state why this is not applicable.

### Deployment and operations

Describe runtime processes, infrastructure boundaries, configuration, secrets, health, scaling, observability, and recovery when the execution environment is known.

### Cross-cutting concepts

Capture relevant policies shared across components, such as security, validation, error handling, retries, configuration, caching, versioning, testing, and release practices. Add a small diagram where it makes relationships clearer than prose.

## Acceptance criteria

- [ ] <observable behaviour or quality requirement>

## Implementation plan

### 1. <verifiable step>

- Outcome: <what becomes true>
- Likely areas: <existing files/directories, or “new scaffold”>
- Verification: <test, check, or observation>

## Testing strategy

- Unit:
- Integration:
- End-to-end or manual:

## Risks, technical debt, and mitigations

- Risk: <failure mode> — Mitigation: <response>
- Deliberate debt: <shortcut, consequence, and follow-up condition>

## Rollout, migration, and rollback

State what is required, or explain why it is not applicable.

## Vocabulary

Define only domain or technical terms that could be ambiguous.

## Completion notes

Record material deviations, checks performed, and follow-up work when the plan is completed.
