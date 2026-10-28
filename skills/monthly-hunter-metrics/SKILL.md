---
name: monthly-hunter-metrics
description: "Compute a small monthly metric set from your own records so progress is measured in accepted findings and response latency rather than in hours felt productive. Use when a month closes and you need evidence about how the practice is actually performing"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [portfolio, metrics, review]
---

# Monthly Hunter Metrics

> Compute a small monthly metric set from your own records so progress is measured in accepted findings and response latency rather than in hours felt productive

**Use when:** a month closes and you need evidence about how the practice is actually performing

**Avoid when:** you have fewer than a handful of reports in a period and the numbers would be noise

## Procedure

1. Define a fixed metric set: reports submitted, accepted, rejected, duplicate rate, median first response, bounties paid.
2. Pull the numbers from your own report log rather than from memory or platform dashboards alone.
3. Compute the month and compare against your trailing average, marking which movements are noise.
4. Attribute major movements to specific causes: a new program, a changed workflow, a skill gap, or luck.
5. Choose one process change from the largest attributable movement and write it down as an experiment.
6. Keep the metric definition stable across months so trends remain comparable instead of being re-invented.

## Signals

- Duplicate rate rises for a third month, which is a systematic signal rather than a run of bad luck.
- Submission volume is flat while acceptance falls, pointing at targeting rather than effort.
- Median first response lengthens across several programs at once, which suggests industry load rather than your work.
- You cannot attribute a movement to anything, which usually means the metric set is missing a dimension.

## Patterns

**1. Metric row**

```text
submitted=11 accepted=6 dup=3 rejected=2 median-first-response=4d bounties=2150
```

**2. Delta note**

```text
metric=dup-rate prev=0.18 curr=0.27 cause=high-competition-surfaces action=angle-shift-experiment
```

**3. Attribution**

```text
movement=acceptance-down cause=new-program-onboarding evidence=program-b-shows-0-accept-yet
```

## Pitfalls

- Changing metric definitions mid-series, which destroys comparability to manufacture a better-looking trend.
- Celebrating volume while acceptance and duplicate rate degrade underneath it.
- Pulling numbers from memory, which systematically rounds in your favor.
- Deriving an action for every movement, including the ones that are pure noise in a small sample.

## Done when

- The fixed metric set is computed from your log with the month-over-month comparison written down.
- Major movements have attributed causes and noise is labeled as noise.
- One process change is recorded as an experiment with a defined next review.

## References

- [FIRST - Common Vulnerability Scoring System](https://www.first.org/cvss/)
- [CWE - weakness catalog for classification counts](https://cwe.mitre.org/)
