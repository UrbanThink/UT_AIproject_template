---
name: ship-feature
description: Take a feature from request to shippable state using the ship-feature skill workflow.
argument-hint: Describe the feature, expected behavior, constraints, and affected area.
agent: Planner
---

Your task is to ship a feature using the **ship-feature** skill.

Load and follow the full workflow defined in `.github/skills/ship-feature/SKILL.md`.

Use the [checklist](.github/skills/ship-feature/checklist.md) to verify completeness before finishing.

Use the [PR summary template](.github/skills/ship-feature/templates/pr-summary.md) for the final output.

Rules:

- keep changes minimal and coherent
- preserve documented architecture and surrounding patterns
- do not skip tests when behavior changes
- explicitly flag breaking changes, risky migrations, and security-sensitive updates
- do not treat “it compiles” as sufficient evidence of quality