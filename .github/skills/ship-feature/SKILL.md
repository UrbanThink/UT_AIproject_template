---
name: ship-feature
description: End-to-end workflow for taking a feature from request to shippable state with planning, implementation, tests, review, and final release readiness checks. Use this for any non-trivial feature that changes behavior.
argument-hint: "[feature request] [acceptance criteria] [constraints]"
---

# Ship Feature

Use this skill when a request requires more than a tiny localized edit and should be handled with a structured implementation workflow.

This skill is designed to help the agent:

- understand the feature request
- inspect the existing codebase before coding
- produce a minimal implementation plan
- implement the smallest safe solution
- add or update tests
- review the change critically
- prepare a concise final summary for human review

Related resources:

- [workflow checklist](./checklist.md)
- [PR summary template](./templates/pr-summary.md)

## When to use this skill

Use this skill when:

- adding a new feature
- extending an existing feature
- changing user-visible or API-visible behavior
- modifying behavior in a way that needs tests and review
- working across multiple files or layers

Do not use this skill for:

- trivial typo fixes
- single-line cosmetic changes
- purely mechanical formatting edits
- isolated test-only edits with no behavior change

## Operating principles

- inspect existing patterns before introducing new ones
- prefer the smallest safe implementation
- preserve backward compatibility unless explicitly asked otherwise
- keep the diff coherent and reviewable
- update tests when behavior changes
- surface assumptions, risks, and tradeoffs explicitly

## Execution workflow

### Step 1 - Frame the request

Restate the request in precise terms:

- what should change
- what should remain unchanged
- who or what consumes the behavior
- what constraints matter
- what acceptance criteria are explicit or implied

If acceptance criteria are missing, infer the minimum safe interpretation and state assumptions clearly.

### Step 2 - Inspect the existing code

Before proposing implementation:

- inspect nearby modules
- find similar features or flows
- inspect existing tests around the affected area
- identify local conventions that should be reused
- identify whether the request touches backend, frontend, data, infra, or multiple layers

Do not propose architecture in the abstract.  
Ground the plan in actual repository structure.

### Step 3 - Plan minimally

Produce a small implementation plan that includes:

- impacted files or modules
- behavior changes
- non-goals
- compatibility concerns
- test strategy
- security or operational implications if relevant

Prefer incremental changes over broad rewrites.

### Step 4 - Implement

Implement the smallest safe version that satisfies the request.

Implementation expectations:

- keep functions and modules focused
- preserve naming and local structure conventions
- avoid broad refactors
- avoid hidden side effects
- preserve unrelated behavior
- update docs if usage or behavior changes materially

### Step 5 - Add or update tests

When behavior changes:

- add or update tests
- protect main success path
- cover important failure path
- cover realistic edge cases
- include regression protection where relevant

Prefer a few strong tests over many weak ones.

### Step 6 - Review critically

Review the result for:

- correctness
- missing cases
- regressions
- architecture drift
- maintainability
- security concerns
- operational concerns where relevant

If weaknesses are found, fix them before considering the work done.

### Step 7 - Prepare final output

End with a concise summary covering:

- what changed
- why it changed
- what was validated
- what remains risky or assumed
- what a human reviewer should pay attention to

Use the [PR summary template](./templates/pr-summary.md) when useful.

## Required output format

Unless the user explicitly wants raw code only, the final output should include:

1. short summary
2. changed areas or files
3. behavior impact
4. tests added or updated
5. remaining risks or assumptions

## Anti-patterns

Avoid:

- coding before inspecting existing patterns
- broad cleanup mixed into feature work
- changing contracts without calling it out
- adding abstractions with no immediate need
- skipping tests on changed behavior
- claiming completeness without validation

## Success criteria

This skill is successful when the delivered feature is:

- aligned with the repository
- minimal in scope
- tested proportionately
- easy to review
- explicit about assumptions and risks