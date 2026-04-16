# Repository AI Instructions

Apply these instructions to all coding tasks in this repository.

## General behavior

- Understand the task before modifying code.
- Inspect existing code patterns before introducing new abstractions.
- Prefer small, reviewable, reversible changes.
- Preserve consistency with the surrounding codebase.
- Do not perform broad refactors unless clearly required.
- Surface assumptions and risks explicitly when they matter.

## Code quality

- Write clear, readable, maintainable code.
- Prefer explicit behavior over clever shortcuts.
- Keep functions and modules focused on one responsibility.
- Avoid unnecessary indirection, premature abstraction, and dead code.
- Reuse existing utilities and patterns when appropriate.
- Keep diffs coherent and easy to review.

## Correctness

- Do not guess behavior that can be derived from existing code or documentation.
- Preserve backward compatibility unless the task explicitly requires a breaking change.
- When changing behavior, identify likely side effects and impacted areas.
- Validate inputs and handle failure paths explicitly.
- Fail predictably rather than silently.

## Testing

See `.github/instructions/tests.instructions.md` for detailed testing rules.

- Add or update tests when behavior changes.
- Keep tests deterministic, readable, and focused on behavior.

## Security

See `.github/instructions/security.instructions.md` for detailed security rules.

- Never hardcode secrets, tokens, passwords, or private keys.
- Validate untrusted input at boundaries.
- Call out security-sensitive changes explicitly.

## Documentation

- Update documentation when behavior, architecture, configuration, or usage changes.
- Keep documentation aligned with the implemented reality.
- Prefer concise and actionable documentation.
- If the task relies on undocumented project knowledge, note the gap clearly.

## Repository context usage

Before making a change:

1. read the relevant task carefully
2. inspect nearby code
3. read applicable scoped instructions in `.github/instructions/`
4. read relevant project documentation in `docs/`
5. follow established repository conventions

## Output expectations

When finishing a task, provide a concise summary covering:

- what changed
- why it changed
- what was validated
- remaining risks or assumptions, if any

## What not to do

- do not invent architecture without checking existing patterns
- do not duplicate logic unnecessarily
- do not add dependencies without clear need
- do not hide uncertainty
- do not bypass tests or checks without explaining why
- do not prioritize speed over reliability or security

## Default mindset

Aim for code that is:

- correct
- simple
- secure
- testable
- maintainable
- easy to review

## Langue des réponses du chat

- **Règle (chat seulement) :** Toutes les réponses destinées au chat doivent être rédigées en français.
- **Portée :** Cette règle s'applique uniquement aux messages conversationnels envoyés dans l'interface du chat (réponses, explications, suggestions, questions de clarification). Elle ne doit pas modifier la langue ni le contenu des fichiers générés par l'agent (code, documentation, templates, ou tout autre artefact de dépôt).

Respectez cette consigne explicitement lors de la formulation des messages destinés à l'utilisateur dans le chat.