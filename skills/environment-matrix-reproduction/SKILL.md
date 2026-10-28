---
name: environment-matrix-reproduction
description: "Reproduce across a deliberate matrix of clients, accounts and configurations so the defect's blast radius is known before you describe it, not discovered during triage. Use when a defect might be environment-specific and you need to state where it does and does not occur"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reproduction, evidence, coverage]
---

# Environment Matrix Reproduction

> Reproduce across a deliberate matrix of clients, accounts and configurations so the defect's blast radius is known before you describe it, not discovered during triage

**Use when:** a defect might be environment-specific and you need to state where it does and does not occur

**Avoid when:** the defect is server-side and identical across every client you can reach

## Procedure

1. Define the matrix dimensions that could plausibly matter: browser, device, account role, plan tier and region.
2. Select a minimal set of cells that separates the dimensions without exploding into full combinatorics.
3. Run the reproduction procedure identically in each cell, changing only the dimension under test.
4. Record a cell-by-cell result table with pass, fail or not-applicable for every combination tried.
5. Identify the boundary: which dimension flips the behavior and which dimensions have no effect.
6. Report the boundary as part of the finding, since the affected-surface claim depends on it.

## Signals

- The defect appears on one browser only, which points at a client-side path and narrows the root cause.
- A paid-tier account does not reproduce while a free-tier account does, marking a tier-dependent branch.
- One region fails while another passes, indicating deployment drift or geo-specific configuration.
- Every cell fails identically, which simplifies the claim and lets you drop the matrix from further work.

## Patterns

**1. Matrix row**

```text
browser=chrome:fail browser=firefox:fail device=mobile:pass role=admin:pass role=member:fail
```

**2. Boundary note**

```text
flipping-dimension=role implication=server-side-role-check root-cause=hypothesis
```

**3. Cell record**

```text
cell=free/tier+eu result=fail n=3 build=2.31.0 vs build=2.30.4 result=pass note=regression-window
```

## Pitfalls

- Testing cells in an order that changes state between them, so later cells inherit mutations from earlier ones.
- Choosing a matrix so large it never completes, which delays the report without improving it.
- Reporting a boundary you did not actually isolate, which invites triage to refute the whole claim.
- Ignoring build versions, so a defect appears to be environment-specific when it is actually time-specific.

## Done when

- A cell-by-cell table exists with every attempted combination labeled pass, fail or not-applicable.
- The dimension that flips the behavior has been isolated or explicitly declared unresolved.
- The affected-surface claim in your finding matches the observed matrix rather than a guess.

## References

- [OWASP - testing guidance for coverage](https://owasp.org/www-project-web-security-testing-guide/)
- [FIRST - Common Vulnerability Scoring System](https://www.first.org/cvss/)
