---
name: init-project
description: Bootstrap a new project from this template by choosing the stack, creating base files, and configuring the development environment.
argument-hint: Describe the project goal, target stack (language, framework, database), and any known constraints.
agent: Planner
---

Your task is to initialize a new project from this repository template.

Follow this workflow:

1. Understand the project goal, target audience, and key constraints.
2. Choose and justify the technology stack (language, framework, database, hosting).
3. Record the stack decision as an ADR in `docs/architecture/decisions/`.
4. Set up the base project structure under `src/` following the chosen framework conventions.
5. Create initial configuration files (package manager, linter, formatter, tsconfig/pyproject, etc.).
6. Configure the CI pipeline in `.github/workflows/ci.yml` for the chosen stack.
7. Update `README.md` with the project name, description, and getting-started instructions.
8. Update `docs/ai/README.md` to note the chosen documentation language (French or English).
9. Update `.vscode/extensions.json` and `.vscode/launch.json` for the chosen stack.
10. Create a minimal "hello world" or health-check endpoint to validate the setup.
11. Add a smoke test to verify the project runs.
12. Hand off to Reviewer for a sanity check on the initialized structure.
13. Summarize:
    - chosen stack and rationale
    - created files
    - configuration decisions
    - what the developer should do next

Rules:

- do not over-engineer the initial setup
- follow the conventions in `.github/instructions/conventions.instructions.md`
- follow the dependency rules in `.github/instructions/dependencies.instructions.md`
- keep the initial dependency count minimal
- ensure `.gitignore` covers the chosen stack
- do not hardcode secrets or environment-specific values
- record significant choices as ADRs
