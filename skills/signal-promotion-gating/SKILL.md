---
name: signal-promotion-gating
description: "Promote a lead from observation to active queue item only when it clears declared evidence gates, so curiosity does not silently convert into committed research hours. Use when recon and passive work keep producing interesting leads that all want immediate testing time"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [queue, triage, signals]
---

# Signal Promotion Gating

> Promote a lead from observation to active queue item only when it clears declared evidence gates, so curiosity does not silently convert into committed research hours

**Use when:** recon and passive work keep producing interesting leads that all want immediate testing time

**Avoid when:** a lead is already a confirmed reproducible issue needing only write-up and submission

## Procedure

1. Define promotion gates in advance: in-scope confirmation, a testable hypothesis, an observable outcome and an effort band.
2. Log every raw lead at observation time with the evidence that produced it, before judging its merits.
3. Apply the gates mechanically at triage, promoting only leads that satisfy every gate on written evidence.
4. Route ungated leads to a holding area with the specific missing gate named for each.
5. Promote only as many leads as the week's capacity admits, ranking gated leads by expected value per hour.
6. Audit promotions afterward to see which gates best predicted productive work, and tighten the ones that did not.

## Signals

- Leads enter the active queue because they are interesting, not because they passed any evidence gate.
- A holding area exists but lacks the specific missing gate named per item, so nothing can be finished later.
- Promotions exceed capacity, which means something already queued is being silently displaced.
- Leads promoted without a testable hypothesis stall at their first session for lack of an observable outcome.

## Patterns

**1. Gate line**

```text
lead=favicon-hash-infra scope=confirmed hypothesis=yes outcome=port-reachable band=quick verdict=promote
```

**2. Hold record**

```text
lead=legacy-backup missing-gate=observable-outcome next=probe-one-path-or-drop
```

**3. Audit note**

```text
promoted=9 produced-finding=2 gate-that-failed=observable-outcome action=tighten-this-gate
```

## Pitfalls

- Treating gates as advisory, which lets the loudest lead bypass the process entirely.
- Promoting past capacity, which displaces ranked work and breaks every estimate already made.
- Holding leads without naming the missing gate, so they rot instead of maturing.
- Never auditing gate performance, keeping gates that predict nothing useful.

## Done when

- Promotion requires every declared gate satisfied on written evidence, with ungated leads parked and specific.
- Promoted work fits within the week's capacity without displacing ranked queue items.
- A gate audit exists showing which gates predicted productive sessions.

## References

- [CWE - weakness catalog for lead classification](https://cwe.mitre.org/)
- [OWASP - testing guidance](https://owasp.org/www-project-web-security-testing-guide/)
