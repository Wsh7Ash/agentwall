---
name: effort-estimate-banding
description: "Estimate research effort in coarse calibrated bands instead of false-precision hours, so queue arithmetic stays honest about how wrong the numbers are allowed to be. Use when you rank work by expected value per hour but your hour estimates are guesses you never check"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [estimation, queue, planning]
---

# Effort Estimate Banding

> Estimate research effort in coarse calibrated bands instead of false-precision hours, so queue arithmetic stays honest about how wrong the numbers are allowed to be

**Use when:** you rank work by expected value per hour but your hour estimates are guesses you never check

**Avoid when:** an engagement is fixed-scope with contractually agreed hours that make estimation moot

## Procedure

1. Define a small set of effort bands, for example quick under an hour, standard a session, deep multiple sessions.
2. Attach observable criteria to each band, such as number of endpoints, need for setup, or need for new tooling.
3. Estimate every queued item by band rather than by hour, refusing to invent precision the work does not support.
4. Compare each band to outcomes after the work completes, tracking whether quick items routinely overrun.
5. Widen or narrow the bands when reality keeps landing outside them, because calibration is the whole point.
6. Use bands plus expected value together, since a deep item must carry a correspondingly larger payoff.

## Signals

- Estimates cluster on suspiciously round numbers, which indicates guesswork rather than decomposition.
- Items estimated as quick repeatedly consume a full session, meaning the band boundaries are wrong.
- You are arguing about whether something takes four or five hours when the difference changes no decision.
- A deep-band item sits at the top of a value-per-hour ranking, which is an arithmetic inconsistency worth fixing.

## Patterns

**1. Band table**

```text
quick=<1h criteria=one-endpoint-known-tooling standard=1-session criteria=new-setup deep=>1-session criteria=env-build
```

**2. Calibration line**

```text
band=quick n=14 overran=6 median-actual=1.8h verdict=band-too-tight-redefine
```

**3. Queue note**

```text
rank=2 item=deep-band ev/hr=220 flag=deep-needs-big-payoff check=confirm-payoff-justifies-band
```

## Pitfalls

- Producing hour-level estimates for work with too many unknowns, then blaming yourself for the variance.
- Never calibrating, so bands encode folklore about your speed instead of measurement.
- Letting a deep-band item outrank everything on per-hour value while ignoring that its cost is concentrated.
- Re-estimating during triage to make a favored item fit the queue, which destroys the estimate's meaning.

## Done when

- Every queued item carries a band with observable criteria rather than a fabricated hour count.
- Band calibration has been compared against completed work at least once.
- Deep-band items appear near the top of the value ranking only with a written justification.

## References

- [OWASP - testing guidance for scoping effort](https://owasp.org/www-project-web-security-testing-guide/)
- [CWE - weakness catalog](https://cwe.mitre.org/)
