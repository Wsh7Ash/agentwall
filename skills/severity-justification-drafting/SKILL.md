---
name: severity-justification-drafting
description: "Derive severity from the program's published criteria with an explicit written rationale per factor, so the number arrives argued rather than asserted and survives the first challenge. Use when the submission requires a severity rating and the program publishes its own scale"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [severity, reporting, triage]
---

# Severity Justification Drafting

> Derive severity from the program's published criteria with an explicit written rationale per factor, so the number arrives argued rather than asserted and survives the first challenge

**Use when:** the submission requires a severity rating and the program publishes its own scale

**Avoid when:** the program assigns severity itself and explicitly asks you not to rate it

## Procedure

1. Read the program's severity definitions verbatim and note the factors each band actually keys on.
2. Score each factor separately from your evidence: attack vector, prerequisites, impact, scope and user interaction.
3. State the reasoning for every factor, including factors you could not test and how you treated them.
4. Compute the band from the factors rather than starting from a gut number and justifying backward.
5. Pre-write the counterargument a skeptic would raise, and answer it inside the rationale.
6. Keep the factor notes with the report so a post-fix re-rating can reuse the same reasoning structure.

## Signals

- The rating was chosen first and the rationale assembled afterward, which reviewers detect quickly.
- Only one factor was considered, usually impact, while prerequisites and interaction were never examined.
- You cannot name the program's own definition of the band you selected.
- An untested factor is silently treated as favorable, inflating the rating without disclosure.

## Patterns

**1. Factor line**

```text
vector=network auth=required interaction=none impact=high-data scope=same band=high note=all-tested
```

**2. Untested note**

```text
factor=rate-limit-at-scale tested=no treatment=assumed-favorable disclosed=yes impact-on-band=none
```

**3. Counter line**

```text
objection=requires-account reply=free-signup-suffices objection=no-impact reply=37-records-per-page-evidenced
```

## Pitfalls

- Starting from the number you want and reverse-engineering factor scores to reach it.
- Treating untested factors as if they had been tested in your favor.
- Citing CVSS or a generic scale when the program publishes its own, which makes your rating irrelevant to them.
- Leaving the counterargument unspoken so triage raises it and wins the exchange by default.

## Done when

- Every severity factor is scored with a one-line rationale drawn from evidence.
- Untested factors are disclosed with their assumed treatment.
- The strongest objection to the rating has a written answer inside the rationale.

## References

- [FIRST - Common Vulnerability Scoring System](https://www.first.org/cvss/)
- [CWE - weakness catalog](https://cwe.mitre.org/)
