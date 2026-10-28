---
name: remediation-guidance-drafting
description: "Offer remediation direction grounded in the root cause you actually observed, framed as guidance rather than instruction, so triage gets a useful starting point without you overstepping. Use when the report is complete and you can identify the likely root cause behind the observed behavior"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reporting, remediation, triage]
---

# Remediation Guidance Drafting

> Offer remediation direction grounded in the root cause you actually observed, framed as guidance rather than instruction, so triage gets a useful starting point without you overstepping

**Use when:** the report is complete and you can identify the likely root cause behind the observed behavior

**Avoid when:** you are guessing at internal architecture you have no evidence for

## Procedure

1. Name the observed defect separately from your hypothesis about the underlying cause, keeping the two distinct.
2. Ground the hypothesis in evidence: which response, which code path signature, which behavior pattern suggested it.
3. Describe the class of fix, such as enforcing an ownership check at a query boundary, without prescribing implementation.
4. Note where else the same class likely appears, since one observed instance usually marks a pattern.
5. Flag anything you tested that suggests a fix would be incomplete, such as a second path with the same behavior.
6. Keep the tone advisory so the owning team can translate guidance into their architecture without contortion.

## Signals

- Your fix suggestion names internal modules or frameworks you have never seen.
- Root cause and observed behavior are stated as the same thing, which hides what is actually inferred.
- A second endpoint shows identical behavior and your guidance addresses only the first.
- Guidance reads as a demand for a specific implementation, which the team is free to reject.

## Patterns

**1. Root-cause line**

```text
observed=object-read-without-ownership-check hypothesis=service-layer-authorization-missing evidence=status-200-with-cross-tenant-body
```

**2. Class note**

```text
fix-class=enforce-ownership-at-data-access-boundary likely-also=invoice-list,endpoint-export tested=invoice-list:yes-also-fails
```

**3. Tone check**

```text
phrasing=suggests-may-worth-checking not=must-implement-x advisory=yes overreach=no
```

## Pitfalls

- Presenting a speculative cause as fact, which the team may implement around instead of verifying.
- Prescribing a specific implementation for an architecture you cannot see.
- Addressing one instance when the same class appears on sibling endpoints you already touched.
- Omitting the second failing path you observed, so the fix ships incomplete.

## Done when

- Observed behavior and hypothesized cause are stated separately with evidence for the hypothesis.
- Guidance describes a fix class rather than an implementation and stays advisory in tone.
- Sibling endpoints with the same behavior are listed as likely same-class instances.

## References

- [CWE - weakness catalog for class-level guidance](https://cwe.mitre.org/)
- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
