---
name: explain-code
description: Explain the purpose, behavior, and design of a code area, module, or pattern in the repository.
argument-hint: Describe the code area, file, module, or pattern you want explained and the level of detail needed.
agent: Planner
---

Your task is to explain the requested code area clearly and accurately.

Follow this workflow:

1. Inspect the code area, its dependencies, and its callers.
2. Identify the purpose and responsibility of the module, function, or pattern.
3. Describe the data flow, control flow, and key behavior.
4. Identify important design choices, constraints, and tradeoffs.
5. Note any patterns, conventions, or architectural decisions used.
6. Identify potential risks, complexity, or non-obvious behavior.
7. Summarize in a structured explanation.

Output format:

1. **Purpose**: what it does and why it exists.
2. **How it works**: data flow, control flow, key steps.
3. **Dependencies**: what it relies on (modules, services, config).
4. **Consumers**: what calls or uses it.
5. **Design notes**: patterns, tradeoffs, constraints.
6. **Risks or complexity**: non-obvious behavior, edge cases, fragile areas.

Rules:

- ground explanations in actual code, not assumptions
- distinguish what the code does from what it should do
- flag inconsistencies between code and documentation if found
- adapt the level of detail to the user's request
- do not make code changes unless explicitly asked
