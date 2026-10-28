---
name: dead-hypothesis-pruning
description: "Remove hypotheses whose assumptions no longer hold, with the falsification evidence recorded, so the queue reflects what is still testable rather than what was once plausible. Use when entries in the queue depend on targets, features or behaviors that have since changed or disappeared"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [queue, triage, backlog]
---

# Dead Hypothesis Pruning

> Remove hypotheses whose assumptions no longer hold, with the falsification evidence recorded, so the queue reflects what is still testable rather than what was once plausible

**Use when:** entries in the queue depend on targets, features or behaviors that have since changed or disappeared

**Avoid when:** an item is merely hard or blocked but its underlying assumption still stands untested

## Procedure

1. For each queue item, state the assumption it depends on and the evidence that would falsify that assumption.
2. Test cheaply whether the assumption still holds, using a single request or a public changelog rather than a full session.
3. Mark falsified items as dead immediately instead of letting them occupy ranked positions.
4. Record what killed the item, with the observation, so future rounds do not resurrect the same idea.
5. Re-check near-miss items whose assumption is weakened but not yet dead, and set a re-evaluation condition.
6. Keep the queue pruned at each triage so dead weight never competes with live work for attention.

## Signals

- An item targets a feature that shipped behind a flag that is now off, making the test unrunnable today.
- The endpoint list changed and the item's named route no longer exists in any current capture.
- A dependency upgrade removed the behavior the item assumed, which a changelog line confirms.
- An item survives solely because nobody has checked its premise since it was written.

## Patterns

**1. Kill line**

```text
item=legacy-csv-export reason=feature-removed-in-2.9 evidence=release-note killed=2026-10-27
```

**2. Weak item**

```text
item=soap-legacy-assumption status=weak evidence=route-returns-404 recheck=when-docs-updated
```

**3. Prune record**

```text
triage=2026-10-27 scanned=23 killed=4 merged=2 survivors=17 next=2026-11-03
```

## Pitfalls

- Killing an item because one probe failed, when the probe itself may have been malformed.
- Deleting killed items without recording the reason, guaranteeing their return in a later round.
- Leaving dead items ranked above live ones, so the queue's ordering becomes fiction.
- Pruning without a re-evaluation condition on weakened items, which loses them permanently by accident.

## Done when

- Every falsified item is marked dead with its killing observation and date recorded.
- Weakened items carry a re-evaluation condition rather than sitting at current rank.
- The surviving queue contains only items whose assumptions currently hold.

## References

- [CWE - weakness catalog](https://cwe.mitre.org/)
- [OWASP - testing guidance](https://owasp.org/www-project-web-security-testing-guide/)
