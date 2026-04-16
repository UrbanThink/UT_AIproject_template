# AI Workspace Guide

## Purpose

This document is the index for the AI customization layer of this repository.

It explains where each type of guidance lives, how files relate to each other, and how to extend the workspace.

It does **not** redefine the rules already written in each file.

---

## Design Principles

1. **One source of truth per rule** — do not duplicate content across files.
2. **Global rules stay short** — only what is true everywhere belongs in global instructions.
3. **Local rules stay scoped** — layer-specific rules go in scoped instruction files.
4. **Separate rules, roles, commands, and workflows** — instructions, agents, prompts, and skills each have a distinct responsibility.
5. **Documentation is runtime context** — AI agents use `docs/` to make correct decisions.

---

## File Index

| File or directory | Type | Responsibility |
|---|---|---|
| `.github/copilot-instructions.md` | Global instructions | Repository-wide coding rules (quality, correctness, output expectations) |
| `.github/instructions/*.instructions.md` | Scoped instructions | Rules for a specific area (backend, frontend, tests, security, infra) |
| `.github/prompts/*.prompt.md` | Prompts | Reusable task launchers (feature, bug, refactor, tests, review, security) |
| `.github/agents/*.agent.md` | Agents | Persistent AI roles with focused behavior and handoffs |
| `.github/skills/<name>/SKILL.md` | Skills | Multi-step reusable workflows with checklists and templates |
| `AGENTS.md` | Operating guide | How agentic work should happen in this repository |
| `docs/` | Project knowledge | Architecture, domain, API, security, quality documentation |

---

## Scoped Instructions

| File | Scope (`applyTo`) |
|---|---|
| `backend.instructions.md` | `src/backend/**`, `src/server/**`, `src/api/**`, `src/services/**`, `app/**`, `server/**` |
| `frontend.instructions.md` | `src/frontend/**`, `src/ui/**`, `src/components/**`, `**/*.tsx`, `**/*.jsx`, `**/*.css` |
| `tests.instructions.md` | `tests/**`, `__tests__/**`, `**/*.test.*`, `**/*.spec.*` |
| `security.instructions.md` | `**/*` (global scope) |
| `conventions.instructions.md` | `**/*` (global scope) |
| `dependencies.instructions.md` | `**/package.json`, `**/requirements*.txt`, `**/pyproject.toml`, lockfiles |
| `infra.instructions.md` | `infra/**`, `scripts/**`, `**/Dockerfile`, `**/*.yml`, `**/*.tf` |

---

## Agents

| Agent | File | Role |
|---|---|---|
| Planner | `planner.agent.md` | Analyze, inspect, plan before coding |
| Builder | `builder.agent.md` | Implement changes minimally and safely |
| Reviewer | `reviewer.agent.md` | Critique for correctness, regressions, architecture fit |
| Tester | `tester.agent.md` | Add, improve, review tests |
| Security Reviewer | `security.agent.md` | Validate trust boundaries, secrets, auth, data flows |

See each `.agent.md` for full behavioral rules, handoffs, and constraints.

---

## Prompts

| Prompt | Agent | Purpose |
|---|---|---|
| `ship-feature.prompt.md` | Planner | Ship a feature using the ship-feature skill workflow |
| `fix-bug.prompt.md` | Planner | Root-cause analysis and safe fix |
| `refactor-module.prompt.md` | Planner | Safe module refactoring |
| `init-project.prompt.md` | Planner | Bootstrap a new project from this template |
| `explain-code.prompt.md` | Planner | Explain code purpose, behavior, and design |
| `add-tests.prompt.md` | Tester | Behavior-focused test coverage |
| `review-code.prompt.md` | Reviewer | Critical code or plan review |
| `harden-security.prompt.md` | Security Reviewer | Security-first analysis |

---

## Skills

| Skill | Purpose |
|---|---|
| `ship-feature` | End-to-end: plan → implement → test → review → summary |
| `debug-incident` | Structured incident debugging: symptoms → root cause → fix → regression protection |
| `release-check` | Final readiness check before merge or deployment |

Each skill includes a `SKILL.md`, a `checklist.md`, and optionally `templates/`.

---

## Precedence

When multiple files provide guidance:

1. Direct user request
2. Repository code and existing architecture
3. Scoped instructions for the relevant area
4. Global repository instructions
5. Relevant skill for the workflow
6. Prompt file structure

A scoped instruction overrides a global instruction when both apply.  
If documentation and code conflict, surface the inconsistency explicitly.

---

## When to Add a New File

| You want to... | Add a... |
|---|---|
| Add a rule valid everywhere | Global instruction in `copilot-instructions.md` |
| Add a rule for one area | Scoped `.instructions.md` |
| Create a reusable task launcher | `.prompt.md` |
| Define a persistent AI role | `.agent.md` |
| Standardize a multi-step workflow | `skills/<name>/SKILL.md` |
| Document project knowledge | File under `docs/` |

---

## Naming Conventions

- **Instructions**: name by scope — `backend.instructions.md`
- **Prompts**: name by action — `fix-bug.prompt.md`
- **Agents**: name by role — `reviewer.agent.md`
- **Skills**: name by workflow — `ship-feature/`
- **Docs**: name by topic — `threat-model.md`

Avoid vague names (`misc.md`, `notes.md`, `stuff.md`).

---

## Anti-Patterns

- One giant instruction file for everything
- Duplicated rules across instructions, prompts, agents, and docs
- Missing project knowledge that AI needs for correct decisions
- Workflow logic inside prompts instead of skills
- Agent files overloaded with project documentation

---

## Maintenance

Update the relevant files when architecture, security, coding standards, or recurring workflows change.

Keep this workspace concise, current, and non-redundant.

## Practical Maintenance Checklist

When modifying this AI workspace, verify that:

- each file has one clear responsibility
- global rules are still truly global
- scoped rules are not duplicated globally
- prompts remain action-oriented
- agents remain role-oriented
- skills remain workflow-oriented
- documentation reflects the current repository reality
- obsolete files are removed instead of ignored

---

## Summary

This repository organizes AI guidance into five complementary layers:

1. **Global instructions** for universal rules
2. **Scoped instructions** for local technical rules
3. **Prompts** for reusable task entry points
4. **Agents** for persistent AI roles
5. **Skills** for reusable execution workflows

Supporting project knowledge lives in `docs/`.

This file, `docs/ai/README.md`, is the main explanation of how the AI workspace is structured and how to extend it safely.

---

## Quick Reference

| Need | Put it here |
|---|---|
| A rule valid everywhere | `.github/copilot-instructions.md` |
| A rule valid only for one area | `.github/instructions/*.instructions.md` |
| A reusable task launcher | `.github/prompts/*.prompt.md` |
| A persistent AI role | `.github/agents/*.agent.md` |
| A reusable multi-step workflow | `.github/skills/<skill>/SKILL.md` |
| Architecture or domain knowledge | `docs/` |
| High-level agent collaboration guidance | `AGENTS.md` |

---

## Final Rule

If a future contributor asks, "Where should this AI-related guidance live?", the answer should be determined by function:

- rule
- role
- prompt
- workflow
- project knowledge

Choose the file type based on that function, not based on convenience.