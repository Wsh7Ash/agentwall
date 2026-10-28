---
name: weekly-queue-construction
description: "Build the week's queue from a ranked hypothesis backlog with explicit entry criteria, so Monday starts with decided work instead of an open browser and a vague plan. Use when a new week begins and your candidate work exists as scattered notes rather than an ordered list"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [queue, planning, triage]
---

# Weekly Queue Construction

> Build the week's queue from a ranked hypothesis backlog with explicit entry criteria, so Monday starts with decided work instead of an open browser and a vague plan

**Use when:** a new week begins and your candidate work exists as scattered notes rather than an ordered list

**Avoid when:** you have a single committed engagement whose scope already dictates every session this week

## Procedure

1. Collect every open hypothesis, target idea and pending follow-up into one candidate list without ranking yet.
2. Score each candidate on expected value, effort estimate and confidence, using numbers you have used before.
3. Drop anything that cannot be tested this week for reasons you write down, so the drop is a decision, not drift.
4. Order the survivors by expected value per hour, then cut the list at your measured weekly capacity.
5. Attach a session-sized first action to each queued item, because vague entries get skipped under time pressure.
6. Carry unstarted items forward explicitly at the Friday review rather than letting them vanish by default.

## Signals

- Your working list is longer than your measured weekly capacity, which guarantees silent drops.
- Several entries describe goals rather than first actions, so starting any of them requires fresh planning.
- Items have sat unstarted for multiple weeks, which is evidence the scoring is wrong or the item is a distraction.
- Follow-up work from last week has no queue slot, so it will compete with planned sessions for time.

## Patterns

**1. Queue row**

```text
rank=1 item=authz-on-orders ev/hr=180 est=4h conf=medium first-action=replay-traffic-with-mutated-ids
```

**2. Capacity cut**

```text
capacity=14h queued-hours=13h deferred=3-items deferred-note=low-ev-or-blocked-on-access
```

**3. Carry note**

```text
item=graphql-depth ev=120 weeks-idle=3 reason=blocked-on-env action=re-scope-or-drop
```

## Pitfalls

- Queueing more hours than the week contains, then treating the shortfall as failure rather than as bad arithmetic.
- Admitting items that need discovery work before they can start, which stalls the whole list behind one vague entry.
- Letting carry-over items accumulate for months without a decision to re-scope, re-rank or drop them.
- Ranking by excitement so the queue becomes a wish list instead of an expected-value ordering.

## Done when

- The week's queue fits inside measured capacity and every entry names its first session-sized action.
- Dropped and deferred items carry written reasons and a recheck condition.
- Follow-up and retest work occupies an explicit slot rather than competing with planned research.

## References

- [OWASP - testing guidance for coverage planning](https://owasp.org/www-project-web-security-testing-guide/)
- [CWE - weakness catalog for hypothesis classes](https://cwe.mitre.org/)
