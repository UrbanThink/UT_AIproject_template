---
applyTo: "infra/**/*,ops/**/*,deploy/**/*,docker/**/*,k8s/**/*,helm/**/*,terraform/**/*,ansible/**/*,scripts/**/*,**/Dockerfile,**/docker-compose*.yml,**/*.tf,**/*.tfvars,**/*.yml,**/*.yaml"
---

# Infrastructure Instructions

Apply these instructions when working on infrastructure, deployment, containers, CI/CD, automation scripts, environment configuration, or operational tooling.

## Primary goal

Produce infrastructure changes that are:

- safe
- explicit
- repeatable
- observable
- reversible where possible
- appropriate for production operations

## Core behavior

- Prefer incremental, low-risk changes.
- Keep infrastructure changes understandable by operators.
- Preserve a clear separation between build, runtime, configuration, and secrets.
- Avoid hidden side effects in scripts and deployment logic.

## Idempotency and repeatability

- Prefer idempotent operations.
- Ensure scripts and automation behave predictably if run more than once.
- Avoid manual-only assumptions where automation is expected.
- Make preconditions and side effects explicit.

## Environments and configuration

- Do not hardcode environment-specific values unless explicitly intended.
- Read configuration from approved config layers.
- Keep dev, staging, and production concerns clearly separated.
- Avoid configuration drift by encoding expected behavior in versioned files.

## Secrets

- Never store real secrets in source control.
- Use placeholders or references to secret managers or environment variables.
- Do not print secrets in scripts, CI logs, or troubleshooting output.

## Reliability and operations

- Consider startup order, health checks, retries, timeouts, failure modes, and rollback paths.
- Avoid fragile deploy logic that depends on implicit ordering or timing.
- Prefer explicit readiness and liveness behavior where relevant.
- Keep operational diagnostics simple and useful.

## Network and exposure

- Be explicit about exposed ports, ingress, egress, service boundaries, and trust assumptions.
- Avoid unnecessarily broad exposure.
- Document externally reachable surfaces when they change.

## Data and migration safety

- Treat data-destructive operations as high risk.
- Prefer additive or backward-compatible migrations when possible.
- Call out operations that may affect availability, consistency, or recovery.

## CI/CD

- Keep pipelines clear and deterministic.
- Fail fast when correctness checks fail.
- Avoid burying critical validation inside opaque scripts.
- Make quality gates visible.

## Scripts

- Write scripts defensively.
- Handle errors explicitly.
- Avoid dangerous shell behavior without safeguards.
- Add comments for non-obvious operational logic.

## What to avoid

- hidden production assumptions
- non-repeatable manual sequences
- unsafe secret handling
- destructive actions without warning
- brittle deployment timing
- unclear rollback expectations

## Done criteria for infrastructure work

Infrastructure work is not complete unless:

- the change is understandable
- configuration sources are explicit
- secret handling is safe
- operational impact is considered
- rollback or failure behavior is at least identified