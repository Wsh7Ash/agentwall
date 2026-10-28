---
name: earnings-trend-analysis
description: "Analyze bounty income as a trend by program and defect class so effort can be reweighted toward the work that actually pays rather than the work that feels impressive. Use when several months of bounty data exist and you are deciding where next quarter's hours should go"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [portfolio, payout, metrics]
---

# Earnings Trend Analysis

> Analyze bounty income as a trend by program and defect class so effort can be reweighted toward the work that actually pays rather than the work that feels impressive

**Use when:** several months of bounty data exist and you are deciding where next quarter's hours should go

**Avoid when:** payouts are too few or too irregular for any trend to be distinguishable from luck

## Procedure

1. Assemble settled payouts only, excluding offers and pending amounts, with program and defect class attached.
2. Compute income per program and per class, and per research hour where hour tracking exists.
3. Look for concentration, since a single program or class dominating income is both insight and risk.
4. Separate structural changes from one-off events such as a bounty table edit or an exceptional award.
5. Rebalance the next quarter's capacity allocation using income per hour as a primary input.
6. Track concentration risk, and treat a dominant program's decline as a scenario worth planning for.

## Signals

- One program supplies most income while consuming less than most of your hours, which is the strongest signal available.
- A class pays consistently better per hour than the class you spend most sessions on.
- A table change cut income for a class you specialize in, which is structural and requires re-weighting.
- An exceptional award distorts the trend, and treating it as normal wrecks the projection.

## Patterns

**1. Income row**

```text
program=alpha share=0.6 hours=0.35 ev-per-hour=210 program=beta share=0.2 hours=0.4 ev-per-hour=70
```

**2. Concentration**

```text
top-program=0.6 top-class=0.5 risk=high action=cap-at-0.45-next-quarter note=deliberate-diversify
```

**3. Structural flag**

```text
event=bounty-table-edit effect=-35pct-on-class=info-disclosure kind=structural not=one-off
```

## Pitfalls

- Counting pending offers as income, which inflates the trend until they are settled at different amounts.
- Reading one exceptional award as a new baseline and planning capacity around it.
- Ignoring hours, so a high-income program that consumes every session looks better than it earns per hour.
- Letting concentration grow unexamined, because dominant programs can restructure without warning.

## Done when

- Settled income is broken down by program and class with per-hour figures where hours are tracked.
- Concentration is measured and a deliberate cap or diversification decision exists.
- Structural changes are separated from one-off events in the trend reading.

## References

- [FIRST - Common Vulnerability Scoring System](https://www.first.org/cvss/)
- [CWE - weakness catalog](https://cwe.mitre.org/)
