---
name: release-check
description: Final release-readiness workflow for reviewing a change before merge or deployment, with emphasis on correctness, tests, compatibility, operational impact, security-sensitive changes, and reviewer watchpoints. Use this before shipping meaningful changes.
argument-hint: "[change summary] [deployment context] [review focus]"
---

# Release Check

Use this skill to perform a release-readiness pass before merge, deployment, or handoff.

This skill helps the agent verify that a change is not only implemented, but also ready to be shipped responsibly.

Related resources:

- [release checklist](./checklist.md)
- [release notes template](./templates/release-notes.md)

## When to use this skill

Use this skill when:

- a feature is considered complete
- a bug fix is about to be merged
- a risky change needs a final structured review
- a deployment or release needs a disciplined gate
- a human reviewer wants a condensed readiness report

Do not use this skill for:

- very early planning
- incomplete exploratory prototypes
- tasks that have not yet been implemented

## Goals

This skill verifies:

- correctness confidence
- test adequacy
- compatibility and migration awareness
- operational readiness
- security-sensitive implications
- human reviewer visibility on remaining risk

## Execution workflow

### Step 1 - Understand the delivered change

Summarize:

- what changed
- why it changed
- which layers are affected
- whether behavior, contracts, config, or deployment are affected

### Step 2 - Check correctness signals

Inspect whether:

- the implementation matches the request
- changed behavior is coherent
- failure paths were considered
- obvious regressions are addressed
- incompatible changes are called out

### Step 3 - Check validation quality

Verify whether:

- tests were added or updated when needed
- the chosen test level is appropriate
- important edge cases were covered
- regression-prone paths were protected
- there are visible gaps in validation

### Step 4 - Check operational and deployment impact

When relevant, inspect:

- config changes
- migrations
- environment assumptions
- startup or runtime implications
- rollback considerations
- observability and logs
- external integration impact

### Step 5 - Check security-sensitive impact

When relevant, inspect:

- input validation
- auth and permissions
- secret handling
- data exposure
- file or command execution behavior
- logging of sensitive data

### Step 6 - Prepare a release-readiness summary

Produce a concise conclusion with:

- readiness assessment
- blocking issues
- non-blocking watchpoints
- reviewer attention areas
- human checks still recommended before ship

Use the [release notes template](./templates/release-notes.md) when useful.

## Output format

Structure the output as:

1. release readiness assessment
2. what changed
3. validation status
4. deployment or operational watchpoints
5. security watchpoints if any
6. blocker list
7. recommended human review focus

## Readiness levels

Use one of these explicit readiness states:

- ready
- ready with watchpoints
- not ready

Do not imply readiness vaguely.

## Anti-patterns

Avoid:

- treating implementation completion as release readiness
- ignoring migration or config impact
- ignoring missing tests on changed behavior
- burying blockers inside long commentary
- failing to distinguish blockers from follow-up improvements

## Success criteria

This skill is successful when a human can quickly understand:

- whether the change is ready
- what could still go wrong
- what needs attention before ship