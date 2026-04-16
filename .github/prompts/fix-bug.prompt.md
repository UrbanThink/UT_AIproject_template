---
name: fix-bug
description: Analyze a bug, identify the root cause, implement the safest fix, and protect against regression.
argument-hint: Describe the bug, symptoms, reproduction steps, expected behavior, and suspected area.
agent: Planner
---

Your task is to fix a bug with a root-cause-first approach.

Follow this workflow:

1. Restate the bug in terms of expected versus actual behavior.
2. Inspect the relevant code paths and existing tests.
3. Identify the most likely root cause.
4. Confirm whether the bug is local or symptomatic of a wider design issue.
5. Propose the smallest safe fix.
6. Hand off to the Builder agent to implement the fix.
7. Hand off to the Tester agent to add or update regression tests.
8. Summarize the root cause, fix strategy, validation, and remaining risks.

Rules:

- do not patch symptoms without identifying the underlying cause
- do not broaden scope unless the code proves it is necessary
- add or update a regression test whenever feasible
- call out any user-visible contract change explicitly
- surface uncertainty instead of pretending certainty