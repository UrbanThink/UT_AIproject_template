---
applyTo: "**/*"
---

# Conventions Instructions

Apply these conventions across the entire repository for consistency between human developers and AI agents.

## Language conventions

- **Code**: all identifiers, comments, commit messages, and code documentation in English.
- **User-facing documentation**: French or English depending on the project. State the choice in `docs/ai/README.md` when starting a project.
- **Chat responses**: follow the language rule in `.github/copilot-instructions.md`.

## Naming conventions

### Files and directories
- Use `kebab-case` for files and directories: `user-service.ts`, `auth-middleware.py`.
- Use the suffix conventions established by the framework or language in use.
- Test files: `<name>.test.<ext>` or `test_<name>.<ext>` depending on the language.

### Code identifiers
- Follow the dominant convention of the language:
  - JavaScript/TypeScript: `camelCase` for variables/functions, `PascalCase` for classes/types/components.
  - Python: `snake_case` for variables/functions, `PascalCase` for classes.
  - CSS/SCSS: `kebab-case` for class names and custom properties.
- When the project already has established conventions, follow those over these defaults.

### Constants
- Use `UPPER_SNAKE_CASE` for true constants (compile-time or configuration-level).

## Commit messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
type(scope): short imperative description
```

### Types
- `feat`: new feature or behavior
- `fix`: bug fix
- `docs`: documentation only
- `test`: adding or updating tests
- `refactor`: code change that neither fixes a bug nor adds a feature
- `chore`: maintenance, dependencies, tooling
- `ci`: CI/CD pipeline changes
- `style`: formatting, whitespace (no logic change)
- `perf`: performance improvement

### Rules
- Subject line: imperative mood, lowercase, no period, max 72 characters.
- Body (optional): explain what and why, not how.
- Footer (optional): reference issues (`Closes #42`), note breaking changes (`BREAKING CHANGE:`).

## Branch naming

```
type/short-description
```

Examples: `feat/user-auth`, `fix/payment-timeout`, `docs/api-reference`, `chore/upgrade-deps`.

- Use lowercase and hyphens.
- Keep branch names short and descriptive.

## Pull request conventions

- Title follows commit message format: `type(scope): description`.
- Description includes: what changed, why, what was validated, remaining risks.
- Link to the related issue when one exists.
- Keep PRs focused on a single concern.

## Code formatting

- Use the project's configured formatter (Prettier, Black, rustfmt, etc.).
- Follow `.editorconfig` for base formatting rules.
- Do not mix formatting changes with behavioral changes in the same commit.

## Import ordering

- Follow the language or framework convention.
- General order: standard library → external dependencies → internal modules.
- Keep imports sorted within each group.

## Comments

- Write comments only when intent is not obvious from the code.
- Prefer self-documenting code over comments.
- Do not leave commented-out code in the codebase.
- Use `TODO:` for tracked follow-ups (reference an issue when possible).
- Use `FIXME:` for known issues requiring attention.
- Do not use `HACK:` or unexplained workarounds without context.
