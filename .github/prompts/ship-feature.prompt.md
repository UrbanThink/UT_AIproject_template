---
name: ship-feature
description: Take a feature from repository-aligned plan to implementation, testing, and final review summary.
argument-hint: Describe the feature, expected behavior, constraints, and affected area.
agent: Planner
---

Your task is to plan and drive the implementation of a feature to a shippable state using the existing repository conventions.

Follow this workflow:

1. analyze the request and inspect the codebase
2. identify impacted files, contracts, and dependencies
3. produce a minimal implementation plan
4. hand off to Builder for implementation
5. hand off to Tester for behavior and regression coverage
6. hand off to Reviewer for a critical final review
7. summarize:
   - what changed
   - what was validated
   - what remains risky
   - what should be checked by a human reviewer before merge

Rules:

- keep changes minimal and coherent
- preserve documented architecture and surrounding patterns
- do not skip tests when behavior changes
- explicitly flag breaking changes, risky migrations, and security-sensitive updates
- do not treat “it compiles” as sufficient evidence of quality