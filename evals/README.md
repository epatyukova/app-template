# Coding-agent evaluation protocol

This optional benchmark evaluates coding agents and harnesses. It is separate from application-level behavioural evaluations.

## Before each task

1. Write one task specification with explicit acceptance criteria.
2. Record the baseline commit and initial check results.
3. Use equivalent repository snapshots, tools, permissions, and environment configuration.
4. Record the harness, provider, exact model identifier, thinking level, and tool versions.
5. Set a manual spending and task-attempt limit. Automatic API retries are not task repair attempts.
6. Assign a non-secret task ID through `PI_EVAL_TASK_ID` when collecting Pi metrics.

## Run

1. Give each harness/model the exact same task description.
2. Keep hidden acceptance tests outside the agent-editable surface.
3. Limit task attempts consistently, for example one implementation and one repair.
4. Do not change tests or evaluation criteria to make a run pass.
5. Do not automatically push, merge, deploy, or mutate external services.

## Evaluate

- Correctness: acceptance tests and independent review.
- Reliability: regression tests, type checks, lint, and formatting.
- Efficiency: elapsed time, tokens, estimated cost, retries, and tool calls.
- Safety: secret handling, scope adherence, and absence of unauthorized external writes.
- Failure class: API, context, reasoning, tool use, tests, environment, or other.

Use `task-results.csv` for reviewed outcomes. Pi writes local run telemetry to `.pi/metrics/usage.jsonl`; join it using `task_id` and `run_id`. Telemetry cost fields are provider estimates, not bills or spending limits.

Repeat important comparisons. A single successful run is not enough evidence for automatic model routing.
