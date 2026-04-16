---
applyTo: "**/*"
---

# Security Instructions

Apply these instructions whenever a task affects authentication, authorization, secrets, user input, data flows, storage, APIs, integrations, file handling, infrastructure, or deployment behavior.

## Primary goal

Default to secure behavior.

Security is not a separate finishing step.  
It must be considered during design, implementation, review, and testing.

## Core rules

- Treat all external input as untrusted.
- Validate input at system boundaries.
- Sanitize or encode output where required by the target context.
- Apply least privilege to access, permissions, and tool usage.
- Prefer deny-by-default over allow-by-default when feasible.
- Make security-sensitive decisions explicit.

## Secrets and credentials

- Never hardcode secrets, tokens, passwords, API keys, certificates, or private keys.
- Never log secrets or include them in fixtures, screenshots, examples, or test data.
- Use approved secret and configuration mechanisms.
- If a secret-like value is required for an example, use an obviously fake placeholder.

## Authentication and authorization

- Do not assume authentication implies authorization.
- Check permissions at the correct boundary.
- Preserve existing access-control patterns unless explicitly changing them.
- Call out any change that affects access scope, role behavior, or trust boundaries.

## Data handling

- Minimize collection, exposure, and retention of sensitive data.
- Do not expose internal identifiers or internals unless required.
- Be careful with file uploads, downloads, export features, logs, cache, and analytics payloads.
- Avoid insecure client-side assumptions about protected data.

## Dangerous behavior

- Avoid unsafe deserialization, command injection patterns, path traversal risks, insecure redirects, weak HTML rendering, and dynamic execution of untrusted content.
- Be careful with shell commands, filesystem access, temporary files, and generated URLs.
- Do not weaken security controls for convenience without clearly flagging the tradeoff.

## Dependencies

- Do not add a dependency without a clear reason.
- Prefer mature, well-understood, minimally scoped dependencies.
- Be cautious with packages that expand attack surface or duplicate existing platform capabilities.

## Error handling and logging

- Fail safely.
- Avoid leaking stack traces, secrets, or internal details to end users.
- Keep operational logs useful without exposing sensitive data.
- Surface suspicious states explicitly rather than masking them.

## Security review expectations

When a change touches security-sensitive areas:

- identify trust boundaries
- identify new inputs and outputs
- identify permission implications
- identify secret-handling implications
- identify abuse or misuse paths
- add or update tests where appropriate

## What to avoid

- implicit trust
- hidden privilege escalation
- permissive defaults without justification
- convenience shortcuts that bypass validation
- insecure sample code copied into production paths
- silent fallback behavior in sensitive flows

## Done criteria for security-sensitive work

Security-sensitive work is not complete unless:

- inputs are treated as untrusted
- secrets are protected
- access control implications are reviewed
- sensitive outputs are controlled
- security-relevant risks are surfaced explicitly