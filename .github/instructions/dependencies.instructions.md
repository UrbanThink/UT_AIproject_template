---
applyTo: "**/package.json,**/package-lock.json,**/yarn.lock,**/pnpm-lock.yaml,**/requirements*.txt,**/Pipfile,**/pyproject.toml,**/poetry.lock,**/Cargo.toml,**/Cargo.lock,**/go.mod,**/go.sum,**/Gemfile,**/Gemfile.lock,**/*.csproj,**/packages.config"
---

# Dependencies Instructions

Apply these instructions when adding, updating, or removing project dependencies.

## Primary goal

Keep the dependency tree minimal, secure, well-understood, and explicitly justified.

## Adding a dependency

Before adding any new dependency:

1. **Justify the need.** Explain why existing code or standard library cannot solve the problem.
2. **Evaluate the package.** Prefer dependencies that are:
   - mature and actively maintained
   - widely adopted with a clear security track record
   - minimally scoped (do one thing well)
   - well-documented
3. **Check for duplicates.** Do not add a package that overlaps significantly with an existing dependency.
4. **Check the license.** Ensure the license is compatible with the project.
5. **Prefer standard library** when the functionality is available without a third-party package.

## Version management

- Always use a lockfile (`package-lock.json`, `poetry.lock`, `Cargo.lock`, etc.).
- Pin versions or use tight ranges to avoid unexpected breaking upgrades.
- Commit the lockfile alongside dependency changes.
- Do not use `latest`, `*`, or unbounded version ranges in production dependencies.

## Security

- Run security audits regularly (`npm audit`, `pip audit`, `cargo audit`, etc.).
- Address known vulnerabilities promptly.
- Do not ignore audit warnings without explicit justification.
- Be cautious with packages that:
  - request broad system permissions
  - include native binaries
  - have few maintainers or unclear provenance
  - were recently published with no track record

## Updating dependencies

- Update dependencies intentionally, not as a side effect of other work.
- Review changelogs for breaking changes before updating.
- Run tests after dependency updates to verify compatibility.
- Prefer incremental updates over mass-upgrade operations.

## Removing dependencies

- Remove unused dependencies promptly.
- Verify that removal does not break transitive dependency expectations.
- Clean up related configuration, imports, and types.

## Dev vs production dependencies

- Separate development-only dependencies from production dependencies.
- Do not include test frameworks, linters, or build tools in production bundles.

## What to avoid

- Adding a dependency for trivial functionality (e.g., `is-odd`, `left-pad`).
- Adding multiple packages that solve the same problem.
- Ignoring security audit results.
- Committing without updating the lockfile.
- Using packages with known supply-chain risks without mitigation.

## Done criteria

Dependency work is not complete unless:

- the dependency is justified
- the lockfile is committed
- the license is compatible
- no known vulnerability is left unaddressed
- tests pass with the updated dependency tree
