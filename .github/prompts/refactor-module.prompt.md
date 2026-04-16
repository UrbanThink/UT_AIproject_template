---
name: refactor-module
description: Refactor a module safely while preserving behavior, reducing complexity, and keeping the change reviewable.
argument-hint: Describe the module, current pain points, refactoring goals, and non-goals.
agent: Planner
---

Your task is to refactor an existing module safely.

Follow this workflow:

1. Inspect the module and the surrounding architecture.
2. Identify the current responsibilities, pain points, and code smells.
3. Determine what behavior must remain unchanged.
4. Define a small-scope refactoring plan with explicit non-goals.
5. Identify tests that must protect behavior during the refactor.
6. Hand off to the Builder agent for implementation.
7. Hand off to the Tester agent to verify or strengthen regression coverage.
8. Summarize what improved, what stayed intentionally unchanged, and any remaining debt.

Rules:

- preserve behavior unless the user explicitly asks for behavioral change
- prefer incremental refactors over rewrites
- reuse existing patterns where possible
- avoid mixing refactor work with unrelated cleanup
- keep the diff understandable for human review