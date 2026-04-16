---
applyTo: "src/backend/**/*,src/server/**/*,src/api/**/*,src/services/**/*,src/repositories/**/*,src/domain/**/*,app/**/*.py,app/**/*.ts,app/**/*.js,server/**/*.py,server/**/*.ts,server/**/*.js"
---

# Backend Instructions

Apply these instructions when working on backend code, APIs, services, domain logic, repositories, workers, or server-side modules.

## Primary goal

Produce backend code that is:

- correct
- explicit
- testable
- resilient
- secure
- easy to maintain

## Architecture behavior

- Follow the existing backend structure before introducing a new one.
- Preserve clear separation between transport, business logic, persistence, and infrastructure concerns.
- Keep controllers, handlers, or routes thin.
- Put business rules in services, use cases, or domain modules.
- Keep persistence logic inside repositories, gateways, or dedicated data access layers.
- Avoid mixing HTTP, SQL, and domain logic in the same function unless the existing local pattern explicitly does so.

## API behavior

- Validate external input at the boundary.
- Normalize and sanitize request data before use.
- Return predictable error shapes.
- Do not leak internal implementation details in API responses.
- Preserve backward compatibility of public contracts unless explicitly asked to change them.
- When changing an API contract, identify all affected callers, tests, and documentation.

## Data and persistence

- Prefer explicit field mapping over implicit magic.
- Avoid hidden side effects in persistence code.
- Be careful with transactions, partial writes, retries, and idempotency.
- Do not silently swallow persistence errors.
- When modifying data access patterns, consider performance impact and query count.
- Avoid introducing N+1 patterns, unnecessary full scans, or wasteful repeated reads.

## Error handling

- Fail explicitly and predictably.
- Use clear error propagation.
- Differentiate expected business errors from unexpected system failures.
- Add contextual information to logs and errors where useful.
- Never expose secrets, tokens, credentials, or sensitive internals in error messages.

## Concurrency and async behavior

- Be explicit about async boundaries.
- Do not block event loops or async workers with avoidable synchronous heavy work.
- Consider race conditions, duplicate processing, retries, and timeout behavior.
- When a workflow can be executed more than once, think about idempotency.

## Logging and observability

- Prefer structured and actionable logs.
- Log meaningful state transitions and failure reasons.
- Avoid noisy logs with little diagnostic value.
- Do not log secrets or sensitive personal data.
- Keep logs useful for debugging production incidents.

## Configuration

- Read configuration from approved environment or config layers.
- Do not hardcode environment-specific values.
- Add safe defaults only when they are truly safe.
- Document new configuration knobs when introduced.

## Migrations and compatibility

- Prefer safe, incremental changes.
- Consider deployment order when changing schema, contracts, or background jobs.
- Avoid changes that require a risky all-at-once release unless explicitly accepted.

## Tests

When backend behavior changes:

- add or update tests
- cover success path, failure path, and key edge cases
- test behavior, not implementation trivia
- keep test setup understandable
- prefer deterministic fixtures and input data

## What to avoid

- fat controllers
- hidden business logic in database or HTTP layers
- silent fallback behavior
- broad refactors without clear need
- magic constants without explanation
- mixing unrelated responsibilities in one module

## Done criteria for backend work

Backend work is not complete unless:

- behavior is explicit
- impacted paths are identified
- validation is handled
- failure paths are considered
- tests are updated appropriately
- security-sensitive implications are called out when relevant