---
name: research-capacity-allocation
description: "Budget research hours across programs and phases as a finite portfolio, so every week spends time deliberately instead of wherever the most interesting thread happens to lead. Use when you run more than one program or more than one research mode at once and time keeps leaking"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [planning, portfolio, capacity]
---

# Research Capacity Allocation

> Budget research hours across programs and phases as a finite portfolio, so every week spends time deliberately instead of wherever the most interesting thread happens to lead

**Use when:** you run more than one program or more than one research mode at once and time keeps leaking

**Avoid when:** you are single-threaded on one engagement with a deadline that already dictates the schedule

## Procedure

1. Measure your real weekly research capacity from the last month of actual sessions rather than from an aspiration.
2. Split capacity into lanes such as new-surface recon, active exploitation, report writing and follow-up handling.
3. Assign hours per lane per program using expected value per hour from your reward analysis as the weighting input.
4. Reserve a fixed contingency fraction for follow-ups and retests, because reactive work always arrives uninvited.
5. Write the allocation down as hours per lane for the coming week, and compare it against how the last week actually went.
6. Adjust the split monthly using realized outcomes, so allocation follows evidence instead of enthusiasm.

## Signals

- Report writing and follow-up handling consume hours that were never allocated to any lane.
- One program quietly absorbs every session because its surface is more interesting, not more valuable.
- Capacity was planned at a level your calendar has never actually produced for four consecutive weeks.
- Recon keeps growing while exploitation shrinks, producing a large backlog of untested hypotheses.

## Patterns

**1. Allocation row**

```text
lane=recon  planned=6h actual=9h lane=exploit planned=8h actual=5h lane=followup planned=2h actual=4h
```

**2. Portfolio line**

```text
program=alpha weight=0.5 program=beta weight=0.3 program=gamma weight=0.2 basis=ev-per-hour
```

**3. Contingency rule**

```text
reserve=15pct-of-week purpose=triage-and-retests trigger=unplanned-overflow-lane
```

## Pitfalls

- Planning capacity from ideal conditions instead of from last month's measured sessions.
- Leaving follow-up unallocated, then letting triage replies silently eat the exploitation budget.
- Rebalancing weekly on noise when the sample size only supports monthly adjustment.
- Treating the plan as a report card rather than as a hypothesis to compare against reality.

## Done when

- The coming week has hours assigned per lane per program, with a contingency fraction reserved.
- Last week's planned-versus-actual comparison is written down with the top variance explained.
- A monthly reweighting date exists so allocation is re-derived from realized outcomes.

## References

- [OWASP - testing guidance for planning coverage](https://owasp.org/www-project-web-security-testing-guide/)
- [FIRST - Common Vulnerability Scoring System](https://www.first.org/cvss/)
