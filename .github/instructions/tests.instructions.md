---
applyTo: "tests/**/*,__tests__/**/*,**/*.test.*,**/*.spec.*,**/test_*.py,**/*_test.py"
---

# Testing Instructions

Apply these instructions when creating, updating, or reviewing automated tests.

## Primary goal

Write tests that are:

- reliable
- deterministic
- focused
- readable
- useful during refactoring
- easy to diagnose when failing

## Test design

- Test observable behavior, not internal implementation details.
- Prefer tests that explain expected system behavior clearly.
- Keep one strong purpose per test.
- Use descriptive test names that communicate scenario and expected result.
- Avoid overly large tests that verify too many things at once.

## Determinism

- Avoid flaky timing assumptions.
- Avoid dependence on external networks or unstable shared environments unless explicitly required.
- Control time, randomness, and external side effects where possible.
- Use stable fixtures and reproducible inputs.

## Coverage expectations

When behavior changes, ensure tests cover:

- the main success path
- important failure paths
- critical edge cases
- regression-prone branches
- security-relevant behavior when applicable

## Test structure

- Prefer clear arrange / act / assert flow.
- Keep fixtures minimal and understandable.
- Reuse test helpers only when they improve clarity.
- Avoid deeply magical helper layers that make tests harder to read.

## Assertions

- Prefer precise assertions over vague truthiness checks.
- Assert on outcomes that matter to users, callers, or system invariants.
- Avoid over-asserting irrelevant details that create fragile tests.

## Mocks and fakes

- Mock only what must be isolated.
- Prefer realistic boundaries over excessive mocking.
- Do not mock so much that the test stops representing real behavior.
- Be explicit about why a dependency is mocked.

## Regression discipline

- When fixing a bug, add or update a test that would have caught it.
- When changing behavior intentionally, update old tests to reflect the new contract.
- Remove obsolete tests only when they no longer represent valid behavior.

## Maintainability

- Keep tests readable by another developer without extra explanation.
- Avoid duplication, but do not abstract prematurely.
- Prefer clarity over DRY if abstraction would hide intent.

## What to avoid

- flaky tests
- giant fixtures
- excessive mocking
- assertions tied to irrelevant implementation details
- snapshot sprawl without strong justification
- tests that pass but do not prove anything meaningful

## Done criteria for test work

Test work is not complete unless:

- the scenario is clearly expressed
- the test is deterministic
- assertions are meaningful
- failure messages are actionable
- the test helps protect against future regressions