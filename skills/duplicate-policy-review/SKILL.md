---
name: duplicate-policy-review
description: "Understand how a program treats duplicates, race conditions and partial findings before you hunt, because duplicate rules decide whether popular surfaces are worth your hours at all. Use when evaluating a program whose scope covers heavily hunted asset classes like login or payment flows"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [duplicates, payout, program-selection]
---

# Duplicate Policy Review

> Understand how a program treats duplicates, race conditions and partial findings before you hunt, because duplicate rules decide whether popular surfaces are worth your hours at all

**Use when:** evaluating a program whose scope covers heavily hunted asset classes like login or payment flows

**Avoid when:** the program pays partial credit for near-duplicates and you plan to work low-competition surfaces

## Procedure

1. Locate the duplicate rule in the policy and platform page, quoting it verbatim in your notes.
2. Determine whether first-submitted or first-confirmed wins, because the two reward entirely different working styles.
3. Check what partial credit exists for unique variants, such as a different root cause reaching the same impact.
4. Estimate crowd density from the program's public bounty count versus its scope size and popularity.
5. Decide whether to race on popular surfaces or to pursue angles where fewer hunters can arrive first.
6. Log the rule and your strategy choice together so later results can be attributed to the decision, not to luck alone.

## Signals

- The rule awards nothing to the second reporter regardless of the quality or completeness of the write-up.
- Partial credit exists only for a distinct root cause, which means symptom variants are pure duplicates.
- Bounty counts are high relative to scope, signalling many active hunters on the most obvious endpoints.
- The rule changed recently, which resets the effective competition for every hunter using last year's assumptions.

## Patterns

**1. Rule line**

```text
dup-rule=first-submitted partial=distinct-root-cause-only racing-rewarded=yes strategy=angles-over-races
```

**2. Density note**

```text
scope=120-hosts bounties=340/12mo crowd=high implication=avoid-generic-flows
```

**3. Variant test**

```text
claim=unique-variant root-cause=same-as-#8821 verdict=partial-credit-likely-no
```

## Pitfalls

- Hunting the most obvious endpoint on a program where the duplicate rule pays the second reporter nothing.
- Assuming partial credit for a variant that shares a root cause, then being disappointed at triage.
- Ignoring that rule changes rewrite the value of everything already in your queue.
- Measuring crowd density from platform ranking alone, which over-weights a handful of very visible hunters.

## Done when

- The duplicate rule is quoted in your notes with your chosen strategy recorded next to it.
- A crowd-density estimate exists for the surfaces you intend to work, with the evidence behind it.
- You can state in one line what variant would still earn credit if your first report duplicates an existing one.

## References

- [CWE - weakness catalog](https://cwe.mitre.org/)
- [OWASP - testing guidance for common weaknesses](https://owasp.org/www-project-web-security-testing-guide/)
