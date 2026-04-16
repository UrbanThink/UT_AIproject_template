---
name: add-tests
description: Add or improve tests for a feature, bug fix, or risky area using behavior-focused coverage.
argument-hint: Describe the behavior, code area, missing coverage, and desired confidence level.
agent: Tester
---

Your task is to add or improve tests for the requested area.

Follow this workflow:

1. Inspect the implementation and nearby tests.
2. Identify the important behaviors that should be protected.
3. Choose the right test level for the risk and scope.
4. Add or update tests for main path, failure path, and meaningful edge cases.
5. Minimize flakiness and unnecessary mocking.
6. Summarize what is now covered and what still remains untested.

Rules:

- test behavior, not private implementation details
- prefer deterministic inputs and explicit assertions
- keep tests readable and purposeful
- avoid writing tests that merely increase count without increasing confidence