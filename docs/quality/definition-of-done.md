# Definition of Done

A change is considered done when all applicable criteria are met.

## Code quality
- [ ] Code is clear, explicit, and consistent with surrounding patterns.
- [ ] No dead code, magic constants, or unnecessary abstractions introduced.
- [ ] Naming follows project conventions.

## Correctness
- [ ] Main behavior path works as expected.
- [ ] Important failure paths are handled.
- [ ] Edge cases relevant to the change are considered.
- [ ] Backward compatibility is preserved unless explicitly intended otherwise.

## Tests
- [ ] Tests are added or updated when behavior changes.
- [ ] Tests are deterministic, readable, and focused on behavior.
- [ ] Regression protection exists for bug fixes.

## Security
- [ ] Untrusted input is validated at boundaries.
- [ ] No secrets, tokens, or credentials are hardcoded.
- [ ] Auth and permission implications are reviewed when relevant.
- [ ] Sensitive data is not leaked in logs, errors, or responses.

## Documentation
- [ ] Documentation is updated when behavior, configuration, or usage changes.
- [ ] Architecture decisions are recorded when significant choices are made.

## Review
- [ ] The diff is minimal, coherent, and easy to review.
- [ ] Remaining risks or assumptions are stated explicitly.
- [ ] CI checks pass.
