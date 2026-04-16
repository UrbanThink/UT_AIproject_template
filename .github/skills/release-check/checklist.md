# Release Check Checklist

## Change understanding
- [ ] The delivered change is summarized clearly
- [ ] Affected layers are identified
- [ ] Behavior, contract, config, or deployment impact is identified

## Correctness
- [ ] The implementation appears aligned with the request
- [ ] Important failure paths were considered
- [ ] Regressions were reviewed
- [ ] Breaking changes are explicitly called out if present

## Validation
- [ ] Tests were added or updated where needed
- [ ] Validation depth matches the risk level
- [ ] Important edge cases were considered
- [ ] Remaining validation gaps are visible

## Operational impact
- [ ] Config changes are identified
- [ ] Migration implications are identified
- [ ] Runtime or deployment assumptions are identified
- [ ] Rollback implications are at least acknowledged

## Security
- [ ] Security-sensitive changes were reviewed where relevant
- [ ] Input and output handling were considered
- [ ] Secrets or permissions implications were considered
- [ ] Sensitive logging or exposure risks were considered

## Final gate
- [ ] Readiness status is explicit
- [ ] Blocking issues are separated from watchpoints
- [ ] Human review focus areas are listed clearly