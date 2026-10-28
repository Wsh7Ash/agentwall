---
name: impact-quantification-framing
description: "Translate a technical observation into concrete business and user impact with numbers where honest numbers exist, because severity negotiations are won on impact, not on request cleverness. Use when the defect is confirmed and you must state what it costs in terms the program values"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reporting, severity, impact]
---

# Impact Quantification Framing

> Translate a technical observation into concrete business and user impact with numbers where honest numbers exist, because severity negotiations are won on impact, not on request cleverness

**Use when:** the defect is confirmed and you must state what it costs in terms the program values

**Avoid when:** quantification would require speculation you cannot ground in observed data

## Procedure

1. State the primary harm concretely: what data, what action or what money is affected, and for whom.
2. Quantify with observed facts: row counts visible, records per response, accounts affected by the boundary.
3. Bound the claim honestly, naming what you did not test and what an attacker would still need.
4. Distinguish demonstrated impact from plausible-but-untested impact and label each part of the report accordingly.
5. Map the framed impact onto the program's severity scale with one line of reasoning per criterion.
6. Keep a copy of the numbers you asserted so a later re-test can confirm they still hold after fixes.

## Signals

- Your impact section restates the request mechanics without ever saying what a victim loses.
- Numbers in the draft come from extrapolation you have not verified against a single observed sample.
- Severity is asserted without mapping to the program's published criteria.
- Demonstrated and speculative impact are interleaved, so a reviewer cannot tell which is which.

## Patterns

**1. Impact line**

```text
observed=37-invoices-per-page pages=2 boundary=cross-tenant demonstrated=full-untested=bulk-export
```

**2. Bound note**

```text
attacker-needs=valid-account-and-target-id untested=rate-limits-at-scale verdict=state-explicitly
```

**3. Severity map**

```text
criteria=data-exposure=high criteria=requires-auth=low criteria=user-interaction=none final=high rationale=one-line
```

## Pitfalls

- Inflating with hypotheticals, which lets triage discount the entire report on one overstated number.
- Measuring only the easy number and omitting the one that actually drives the program's severity scale.
- Framing impact as a vulnerability category rather than as a loss, which invites default-severity assignment.
- Forgetting the numbers you asserted, so a post-fix re-test contradicts your original claim.

## Done when

- Impact states concretely what a victim or the business loses, with observed numbers where they exist.
- Demonstrated and untested impact are visibly separated.
- Severity maps to the program's own criteria with a one-line rationale per criterion.

## References

- [FIRST - Common Vulnerability Scoring System](https://www.first.org/cvss/)
- [CWE - weakness catalog](https://cwe.mitre.org/)
