# Debug Incident Checklist

## Framing
- [ ] The symptom is described clearly
- [ ] Expected behavior is stated
- [ ] Known reproduction conditions are captured
- [ ] Facts are separated from assumptions

## Investigation
- [ ] Relevant code paths were inspected
- [ ] Existing tests near the failing path were inspected
- [ ] Recent changes or likely triggers were considered
- [ ] The likely blast radius was considered

## Root cause
- [ ] A root-cause hypothesis is stated explicitly
- [ ] The hypothesis explains the observed symptoms
- [ ] The issue is classified appropriately: logic, data, config, integration, timing, contract, or state

## Fix
- [ ] The proposed fix addresses root cause, not just symptom
- [ ] The scope of the fix is minimal
- [ ] Unrelated behavior is preserved
- [ ] Risky fallback behavior was avoided

## Regression protection
- [ ] A regression test was added or updated when feasible
- [ ] Similar code paths were checked for the same failure mode
- [ ] Remaining untested risk is called out explicitly

## Summary
- [ ] Root cause is explained clearly
- [ ] Changed areas are listed
- [ ] Validation is described
- [ ] Remaining risks or follow-up actions are stated