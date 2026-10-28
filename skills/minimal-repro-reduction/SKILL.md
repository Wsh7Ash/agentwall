---
name: minimal-repro-reduction
description: "Reduce a working reproduction to the smallest set of steps, fields and state that still triggers the defect, because triage trusts short repros and abandons long ones. Use when your working reproduction contains exploratory steps, extra fields and state that may not be required"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reproduction, evidence, triage]
---

# Minimal Repro Reduction

> Reduce a working reproduction to the smallest set of steps, fields and state that still triggers the defect, because triage trusts short repros and abandons long ones

**Use when:** your working reproduction contains exploratory steps, extra fields and state that may not be required

**Avoid when:** every step in the chain has already been shown to be load-bearing

## Procedure

1. Start from the full working reproduction and identify each step, field and precondition it contains.
2. Remove one element at a time, retesting after each removal, and keep the removal only if the defect still triggers.
3. Record what each removed element actually contributed, since some elements affect severity rather than reproducibility.
4. Repeat until no further removal keeps the defect alive, producing the minimal failing sequence.
5. Verify the minimal version reproduces twice from clean state before adopting it as the canonical repro.
6. Attach both versions when reporting: minimal for triage speed, full for context on how it was found.

## Signals

- The reproduction works with fields that are plainly irrelevant to the defect, which dilutes the signal.
- Triage asked which step is actually required and you cannot answer without doing the reduction.
- Removal of an element changes the response in a way that matters for severity even though the defect persists.
- The minimal version reproduces where the bloated version sometimes fails, because fewer moving parts drift.

## Patterns

**1. Reduction log**

```text
removed=param-referral result=still-fails kept=param-id result=required removed=step-3 result=required
```

**2. Minimal line**

```text
state=member session=fresh request=GET /api/v2/orders/{id} of other user expect=403 got=200
```

**3. Contribution note**

```text
element=extra-header effect=not-required-for-repro but=changes-status-code-from-404-to-403
```

## Pitfalls

- Removing elements in bulk, which destroys attribution and can break a reproduction you cannot rebuild.
- Confusing required-for-repro with required-for-impact, dropping a detail that changes the severity story.
- Adopting the minimal repro without retesting it twice, so you ship a flaky reduction.
- Keeping the bloated version as canonical because reducing it feels like optional polish.

## Done when

- No element can be removed while the defect still triggers, and the minimal repro reproduces twice.
- Each discarded element has a recorded note on what it contributed.
- The report carries the minimal sequence with the full exploration available as supporting context.

## References

- [OWASP - testing guidance for reproduction quality](https://owasp.org/www-project-web-security-testing-guide/)
- [CWE - weakness catalog](https://cwe.mitre.org/)
