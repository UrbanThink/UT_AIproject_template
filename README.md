# Project Name

Short project description.

This repository is designed for high-quality AI-assisted development with GitHub Copilot, VS Code agents, and compatible coding assistants.

## AI workspace

The repository includes a dedicated AI customization layer to improve development speed, consistency, reliability, and security.

Main entry point:

- `docs/ai/README.md`

This document explains:

- how AI instructions are organized
- where to put prompts, agents, and skills
- how developers should extend the AI workspace
- how AI systems should use repository context

## Main repository areas

- `.github/copilot-instructions.md`  
  Global rules for AI coding assistants

- `.github/instructions/`  
  Scoped instructions by technical area

- `.github/prompts/`  
  Reusable prompts for recurring tasks

- `.github/agents/`  
  Persistent AI roles

- `.github/skills/`  
  Reusable multi-step workflows

- `docs/`  
  Architecture, domain, API, security, and quality documentation

- `AGENTS.md`  
  High-level agent operating guide for this repository

## Development principles

This project follows a few core principles:

- prefer small and reviewable changes
- preserve clarity over cleverness
- use existing patterns before introducing new abstractions
- keep behavior explicit
- protect security, reliability, and maintainability by default
- document important decisions close to the codebase

## Getting started

1. Read `docs/ai/README.md`
2. Read `AGENTS.md`
3. Read the relevant files under `docs/`
4. Read the applicable scoped instructions in `.github/instructions/`
5. Follow existing code patterns before changing architecture

## Contributing

Before opening a pull request:

- run formatting, linting, and tests
- verify that changes are minimal and coherent
- update documentation when behavior or architecture changes
- add or update tests when behavior changes
- check whether a new rule belongs in instructions, docs, prompt files, or skills

See also:

- `CONTRIBUTING.md`
- `docs/quality/definition-of-done.md`
- `docs/architecture/overview.md`

## AI usage rule

AI assistance is expected to improve delivery quality, not bypass engineering discipline.

All generated code must still be reviewed for:

- correctness
- maintainability
- security
- test coverage
- architectural consistency

## Utiliser ce dépôt comme template GitHub

Ce dépôt peut servir de template pour créer rapidement de nouveaux projets suivant les bonnes pratiques du groupe.

- Pour créer un nouveau dépôt depuis ce template via l'interface GitHub : cliquez sur **Use this template** puis **Create a new repository**.
- Pour créer et publier le dépôt localement avec la CLI GitHub (`gh`), depuis la racine du projet :

```powershell
gh repo create UrbanThink/UT_AIproject_template --public --source=. --remote=origin --push
gh api -X PATCH /repos/UrbanThink/UT_AIproject_template -f is_template=true
```

Remarques :
- `gh` doit être installé et authentifié (`gh auth login`).
- Le second appel active le dépôt comme template (`is_template=true`).

Checklist avant d'utiliser comme template :

- Supprimer ou remplacer tout secret, clé ou données sensibles.
- Mettre à jour `LICENSE` si nécessaire.
- Compléter `CONTRIBUTING.md` et les templates d'issues/PR sous `.github/`.
- Préparer un dossier `scaffold/` ou des exemples d'initialisation pour démarrer rapidement.

Si vous voulez, je peux :

- auditer le dépôt pour rechercher des secrets potentiels,
- créer automatiquement les fichiers `.github/ISSUE_TEMPLATE` et `PULL_REQUEST_TEMPLATE.md`,
- tenter de créer et d'activer le dépôt sur GitHub via la CLI si `gh` est disponible et authentifié.