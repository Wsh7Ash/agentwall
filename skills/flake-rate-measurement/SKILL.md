---
name: flake-rate-measurement
description: "Measure how often a non-deterministic defect actually fires before reporting it, because an unquantified intermittent bug is the fastest way to lose triage credibility. Use when the defect reproduces sometimes, or depends on timing, concurrency or cached state"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reproduction, evidence, measurement]
---

# Flake Rate Measurement

> Measure how often a non-deterministic defect actually fires before reporting it, because an unquantified intermittent bug is the fastest way to lose triage credibility

**Use when:** the defect reproduces sometimes, or depends on timing, concurrency or cached state

**Avoid when:** the defect fires on every attempt and determinism is already established

## Procedure

1. Define the trial: identical procedure, clean reset between attempts, fixed inputs and environment.
2. Run a meaningful number of attempts, enough that the observed rate means something rather than one in three.
3. Record every attempt with its outcome, timestamp and any variation you noticed, not only the successes.
4. Compute the observed rate and a simple range so the claim is quantified instead of described as intermittent.
5. Vary one suspected factor at a time to see which condition raises or lowers the rate.
6. Report the rate, the trial size and the conditions, so triage knows exactly how hard reproduction will be.

## Signals

- You have reproduced the defect twice and are about to describe it as reliably reproducible.
- Success correlates with load, time of day or cache state, which means conditions matter more than the trigger.
- Triage has already returned it once as cannot-reproduce, which is the cost of an unmeasured rate.
- Attempts were run without reset, so later trials inherit state from earlier ones and the rate is meaningless.

## Patterns

**1. Rate line**

```text
trials=20 fired=6 rate=0.30 window=10m reset=per-trial confidence=rough-not-statistical
```

**2. Factor test**

```text
factor=cold-cache rate=0.60 n=10 factor=warm-cache rate=0.05 n=10 implication=cache-dependent
```

**3. Condition log**

```text
load=high fired=yes load=low fired=no build=2.31.0 note=record-with-report
```

## Pitfalls

- Reporting an intermittent defect with a sample of two, which invites dismissal as anecdote.
- Skipping reset between trials, so the rate measures accumulation rather than the trigger.
- Chasing a larger sample until it looks good, then reporting only the favorable window.
- Measuring rate without varying the obvious condition, leaving the actual driver unexplored.

## Done when

- A trial count, fire count and observed rate are recorded with the exact conditions.
- At least one suspected condition has been varied and its effect on the rate noted.
- The report states the rate plainly so triage can plan its own reproduction attempt.

## References

- [OWASP - testing guidance for reliability](https://owasp.org/www-project-web-security-testing-guide/)
- [FIRST - Common Vulnerability Scoring System](https://www.first.org/cvss/)
