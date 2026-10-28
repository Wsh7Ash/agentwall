---
name: cross-account-reproduction
description: "Prove a finding across distinct accounts and tenants so ownership and isolation claims rest on two independent identities rather than on one session's confused state. Use when the defect concerns access, isolation or ownership between users, tenants or roles"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reproduction, authorization, evidence]
---

# Cross Account Reproduction

> Prove a finding across distinct accounts and tenants so ownership and isolation claims rest on two independent identities rather than on one session's confused state

**Use when:** the defect concerns access, isolation or ownership between users, tenants or roles

**Avoid when:** the defect is entirely within a single account's own private behavior

## Procedure

1. Create two independent identities with no shared state, groups, teams or administrative links.
2. Establish distinct owned data in each identity so ownership boundaries have something real to cross.
3. Perform the triggering action as one identity and observe its effect on data owned by the other.
4. Reverse the roles and repeat, confirming the boundary is consistently crossed rather than one-directional.
5. Record identifiers for both sides of every crossing so the evidence shows exactly whose object moved.
6. State in the report which direction worked, because asymmetric crossing often indicates a different root cause.

## Signals

- The defect only manifests when both identities share a team, which means the boundary may be intentional.
- A single identity test shows no crossing and the second identity is what makes it observable.
- Crossing occurs in one direction only, which usually points at a specific missing check rather than a general one.
- Identifiers used in the test are also visible to the other party, muddying who observed what.

## Patterns

**1. Cross line**

```text
actor=user-a action=read target=order-owned-by-user-b result=200 leak=order-4471 reversed=also-200
```

**2. Identity table**

```text
id=user-a role=member team=none data=orders[4471] id=user-b role=member team=none data=orders[9922]
```

**3. Direction note**

```text
a->b=leak b->a=no-leak implication=missing-filter-on-one-query-path not=general-authz-collapse
```

## Pitfalls

- Using two accounts that share a group or team, then reporting an isolation break that the product intends.
- Testing only one direction and missing the asymmetry that would refine the root cause.
- Reusing objects from earlier tests whose ownership is already ambiguous.
- Reporting access to your own object as cross-account access because the session got confused.

## Done when

- Two independent identities with distinct owned data have been tested in both directions.
- Every crossing names both identifiers and the exact object that was reached.
- The report states directionality and whether shared-group conditions applied.

## References

- [OWASP - access control testing guidance](https://owasp.org/www-project-web-security-testing-guide/)
- [CWE - access control weaknesses](https://cwe.mitre.org/)
