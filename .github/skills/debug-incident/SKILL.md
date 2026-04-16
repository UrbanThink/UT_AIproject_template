---
name: debug-incident
description: Structured workflow for debugging a production or high-priority incident by framing symptoms, isolating the failing path, identifying root cause, implementing the safest fix, and documenting residual risk. Use this for bugs, outages, broken workflows, or suspicious regressions.
argument-hint: "[symptoms] [expected behavior] [reproduction info] [affected area]"
---

# Debug Incident

Use this skill for debugging incidents, production issues, regressions, broken workflows, or difficult bugs.

This skill helps the agent:

- distinguish symptoms from root cause
- inspect the real failing path
- reduce guesswork
- identify the smallest safe fix
- add regression protection
- document what remains uncertain

Related resources:

- [incident checklist](./checklist.md)
- [incident summary template](./templates/incident-summary.md)

## When to use this skill

Use this skill when:

- a workflow is broken
- an error appears in logs or UI
- a deployment introduced a regression
- an integration stopped working
- a bug is difficult to reproduce or localize
- the impact is high enough that disciplined debugging matters

Do not use this skill for:

- cosmetic copy edits
- intentionally planned feature changes
- broad refactors with no specific incident

## Core debugging rule

Do not patch the visible symptom until the likely root cause is identified.

If certainty is impossible, narrow to the strongest evidence-backed hypothesis and say so explicitly.

## Execution workflow

### Step 1 - Frame the incident

Write down:

- observed symptoms
- expected behavior
- affected user or system path
- known reproduction conditions
- severity and likely blast radius

Separate confirmed facts from assumptions.

### Step 2 - Inspect evidence

Gather evidence from:

- relevant code paths
- nearby tests
- recent changes if known
- logs, errors, traces, or visible failure states
- configuration or environment assumptions if relevant

Look for the narrowest failing path that explains the symptom.

### Step 3 - Isolate likely root cause

Determine:

- what is actually failing
- whether the issue is local or systemic
- whether this is logic, state, config, data, timing, contract, or integration related
- whether a recent change likely triggered it

Do not jump from symptom to patch without this step.

### Step 4 - Propose the safest fix

Choose a fix that:

- addresses the root cause
- minimizes blast radius
- preserves unrelated behavior
- does not introduce hidden fallback behavior
- is understandable and reviewable

Prefer a local, explicit correction over a broad redesign unless the code clearly requires more.

### Step 5 - Add regression protection

When feasible, add or update tests that would have caught the issue.

Regression protection can be:

- unit tests
- integration tests
- contract tests
- assertions or guards where appropriate

### Step 6 - Review residual risk

Check for:

- similar call sites or repeated patterns
- related flows that may fail for the same reason
- compatibility issues
- operational or security implications

### Step 7 - Summarize the outcome

Provide:

- root cause
- fix strategy
- changed areas
- regression coverage
- remaining uncertainty
- recommended follow-up if the incident suggests a deeper issue

Use the [incident summary template](./templates/incident-summary.md) when useful.

## Required output format

Unless the user asks otherwise, produce:

1. incident framing
2. likely root cause
3. proposed or implemented fix
4. tests or validation
5. remaining risks or follow-up suggestions

## Anti-patterns

Avoid:

- symptom-only patching
- broad rewrites under incident pressure
- hidden behavior changes
- vague statements like "should fix it" without reasoning
- skipping regression protection when feasible
- conflating guesswork with evidence

## Success criteria

This skill is successful when the incident response is:

- evidence-based
- minimal in scope
- protective against recurrence
- explicit about residual uncertainty