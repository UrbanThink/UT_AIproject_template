# AGENTS.md

## Purpose

This file explains how agentic work should happen in this repository.

It is intended for both developers and AI systems.

Use it as a concise operating guide.  
Detailed rules belong in:

- `.github/copilot-instructions.md`
- `.github/instructions/`
- `.github/prompts/`
- `.github/agents/`
- `.github/skills/`
- `docs/`

## Core operating rules

### 1. Understand before editing
Before making changes:

- identify the exact goal
- inspect the relevant code area
- read the applicable documentation
- check existing patterns
- identify constraints and risks

Do not invent architecture if the repository already contains a working pattern.

### 2. Prefer the smallest safe change
Default to:

- minimal diff size
- local changes
- explicit behavior
- reversible changes
- reviewable implementation

Avoid broad refactors unless they are required by the task.

### 3. Respect repository structure
Each kind of guidance has a dedicated location:

- global rules -> `.github/copilot-instructions.md`
- scoped technical rules -> `.github/instructions/`
- reusable task launchers -> `.github/prompts/`
- persistent roles -> `.github/agents/`
- reusable workflows -> `.github/skills/`
- project knowledge -> `docs/`

Do not duplicate the same content across multiple layers.

### 4. Follow existing patterns first
When working in a code area:

- inspect similar files
- reuse established conventions
- preserve consistency with neighboring code
- only introduce a new pattern if the current ones are clearly insufficient

### 5. Keep security on by default
Never introduce:

- secrets in code
- unsafe defaults
- unvalidated external input
- silent privilege escalation
- unclear auth or access patterns

When in doubt, choose the safer implementation and document tradeoffs.

### 6. Keep behavior testable
When behavior changes:

- add tests or update existing tests
- cover happy path and relevant edge cases
- avoid brittle tests
- prefer deterministic tests

### 7. Surface uncertainty explicitly
If something is unclear:

- state assumptions
- identify missing information
- highlight risks
- avoid pretending certainty

A visible assumption is better than a hidden mistake.

## Recommended workflow

For most tasks, follow this order:

1. understand the request
2. identify relevant files and systems
3. read global and scoped instructions
4. read relevant documentation in `docs/`
5. inspect existing implementation patterns
6. plan the change
7. implement the smallest safe version
8. validate with tests and checks
9. summarize what changed, why, and what remains risky

## Agent roles

This repository uses specialized agents defined in `.github/agents/`.

| Agent | File | Purpose |
|-------|------|---------|
| Planner | `planner.agent.md` | Understand requests, inspect code, produce safe implementation plans |
| Builder | `builder.agent.md` | Implement changes minimally, preserve conventions |
| Reviewer | `reviewer.agent.md` | Critique changes for correctness, regressions, and architecture fit |
| Tester | `tester.agent.md` | Add, improve, and review tests for changed behavior |
| Security Reviewer | `security.agent.md` | Validate trust boundaries, secrets, auth, and risky data flows |

See each `.agent.md` file for full behavioral rules, handoffs, and constraints.

## Documentation expectations

If an implementation depends on project knowledge, that knowledge should be documented.

Important locations:

- `docs/architecture/`
- `docs/domain/`
- `docs/api/`
- `docs/security/`
- `docs/quality/`

If code and docs disagree, surface the inconsistency explicitly.

## Decision rules for adding AI workspace files

Add a new file only when its responsibility is clear.

### Add a global instruction when
The rule is valid across the whole repository.

### Add a scoped instruction when
The rule is only valid for one area, layer, language, or path group.

### Add a prompt when
A task happens frequently and benefits from a reusable launcher.

### Add an agent when
A role should have a stable behavior and responsibility.

### Add a skill when
A multi-step workflow should be standardized and reused.

### Add documentation when
The information is part of the project knowledge, not just agent behavior.

## Anti-patterns

Avoid the following:

- one giant instruction file for everything
- undocumented architecture assumptions
- duplicate rules in multiple places
- prompts that try to replace documentation
- agents overloaded with project knowledge
- skills used for simple static rules
- large code changes without local pattern review

## Definition of good agentic work

Good agentic work in this repository is:

- grounded in actual code
- aligned with documented architecture
- minimal in scope
- explicit in assumptions
- verified with tests and checks
- secure by default
- easy for a human to review

## Final rule

AI should accelerate disciplined engineering, not replace it.

## Memory files and persistence

Agents should persist long-lived, reviewable facts under the `/memories/` directory. See `.github/instructions/memory.instructions.md` for detailed rules. Key points:

- Maintain a thematic index at `/memories/MEMORY.md` (index by topic, not chronologically).
- Place detailed notes in separate thematic files under `/memories/` (e.g., `/memories/security.md`).
- Follow the mandatory maintenance rule: « Mets à jour ou supprime les souvenirs qui s'avèrent erronés ou obsolètes. N'écris pas de souvenirs en double. »
- Do not store secrets or sensitive information in `/memories/`.
