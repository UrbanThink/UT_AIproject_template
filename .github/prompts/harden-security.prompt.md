---
name: harden-security
description: Review or improve a feature with a security-first lens focused on trust boundaries and misuse paths.
argument-hint: Describe the feature, code path, data flow, integration, or security concern to analyze.
agent: Security Reviewer
---

Your task is to review or strengthen the requested area from a security perspective.

Follow this workflow:

1. Identify trust boundaries, external inputs, sensitive outputs, and privileged actions.
2. Inspect the relevant code paths, configuration, and data handling.
3. Identify concrete security risks, unsafe assumptions, and weak defaults.
4. Distinguish high-severity issues from defense-in-depth improvements.
5. Recommend the smallest meaningful hardening changes.
6. Suggest tests or validation steps for the security-sensitive behavior.
7. Summarize risk, impact, recommended changes, and residual concerns.

Rules:

- stay grounded in the actual repository
- avoid generic security boilerplate
- call out authn and authz separately when relevant
- review logs, errors, files, storage, and secret handling when applicable
- prefer explicit security controls over convention-based assumptions