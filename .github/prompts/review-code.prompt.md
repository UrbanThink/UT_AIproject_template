---
name: review-code
description: Perform a critical review of code or a change plan for correctness, regressions, maintainability, and security.
argument-hint: Describe what should be reviewed, the goal of the change, and any known concerns.
agent: Reviewer
---

Review the provided code, diff, or implementation plan critically.

Structure the review as:

1. overall assessment
2. strengths
3. blocking issues
4. non-blocking improvements
5. missing tests or validation
6. security or operational concerns
7. recommended next actions

Review rules:

- inspect real code and existing patterns before judging
- distinguish blockers from polish
- focus on meaningful correctness and maintainability concerns
- call out likely regressions explicitly
- do not approve weak assumptions without challenge
- avoid generic feedback that does not help the author improve the work