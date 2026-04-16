# Ship Feature Checklist

Use this checklist before considering feature work complete.

## Request understanding
- [ ] The requested change is restated clearly
- [ ] Expected behavior is distinguished from non-goals
- [ ] Key assumptions are visible

## Repository alignment
- [ ] Existing patterns were inspected before implementation
- [ ] The chosen implementation matches local code conventions
- [ ] No unnecessary abstraction was introduced

## Scope control
- [ ] The diff is limited to what the request requires
- [ ] Unrelated refactors were avoided
- [ ] Backward compatibility was considered

## Correctness
- [ ] Main behavior path is implemented
- [ ] Important failure paths were considered
- [ ] Edge cases relevant to the change were considered

## Tests
- [ ] Existing tests were reviewed
- [ ] Tests were added or updated where behavior changed
- [ ] The test strategy is proportionate to risk
- [ ] Regression protection exists when needed

## Security and operations
- [ ] Input validation implications were considered
- [ ] Auth, permissions, or sensitive data implications were reviewed if relevant
- [ ] Operational impact was considered if relevant

## Final review
- [ ] The change is understandable by a human reviewer
- [ ] The summary explains what changed and why
- [ ] Remaining risks or assumptions are explicitly stated