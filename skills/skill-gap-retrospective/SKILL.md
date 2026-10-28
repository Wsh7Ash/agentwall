---
name: skill-gap-retrospective
description: "Turn a quarter's misses and dead ends into a ranked list of skill gaps, so what you practice next is chosen from evidence about where work actually stalled. Use when several investigations died at the same kind of obstacle and you want to name the pattern"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [portfolio, skills, review]
---

# Skill Gap Retrospective

> Turn a quarter's misses and dead ends into a ranked list of skill gaps, so what you practice next is chosen from evidence about where work actually stalled

**Use when:** several investigations died at the same kind of obstacle and you want to name the pattern

**Avoid when:** recent work is varied and no repeated obstacle is visible yet

## Procedure

1. Review every stalled, dropped or rejected item from the period and write down where each one actually stopped.
2. Group the stop points by the capability they required: tooling, protocol knowledge, encoding, writing or patience.
3. Rank groups by frequency multiplied by how much they cost, since the common expensive gap comes first.
4. For the top gap, name a concrete learning action with a deadline rather than an aspiration.
5. Apply the new skill to a queued item immediately, because practice without application decays within weeks.
6. Revisit the retrospective next quarter and check whether the top gap actually moved.

## Signals

- Multiple investigations died at the same protocol or encoding obstacle rather than at the target itself.
- Reports were rejected for a quality reason that repeats, which is a writing gap rather than a finding gap.
- You keep deferring the same learning action across retrospectives, which marks it as mis-sized rather than unimportant.
- Dead items cluster around one capability you have never trained deliberately.

## Patterns

**1. Skill gap row**

```text
gap=graphql-introspection stops=5 cost=high action=build-one-lab-sandbox deadline=2026-11-15
```

**2. Stop map**

```text
stop=encoding-obstacle x4 stop=writing-rejection x3 stop=tooling-broken x2 top=encoding
```

**3. Follow-up**

```text
gap=api-protocol-depth action=two-sessions-weekly applied-to=item-11 review=2027-01-05 moved=yes-or-no
```

## Pitfalls

- Listing aspirations instead of observed stop points, which produces the same list every quarter.
- Choosing the easiest gap to close rather than the one that cost the most work.
- Naming a learning action without a deadline, so it never competes for calendar time.
- Skipping the follow-up check, which is the only part that distinguishes a retrospective from a mood.

## Done when

- Stop points are grouped and ranked by frequency and cost, not by anxiety.
- The top gap has one concrete action with a deadline and a queued item to apply it to.
- Last period's top gap has a recorded verdict on whether it moved.

## References

- [CWE - weakness catalog for skill mapping](https://cwe.mitre.org/)
- [OWASP - testing guidance for capability coverage](https://owasp.org/www-project-web-security-testing-guide/)
