---
name: reward-structure-analysis
description: "Decode how a program actually pays, from bounty tables and duplicate rules to hidden multipliers, so expected value is computed from published terms instead of hoped-for maximums. Use when comparing programs on money and you need expected value rather than an advertised ceiling"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [payout, program-selection, planning]
---

# Reward Structure Analysis

> Decode how a program actually pays, from bounty tables and duplicate rules to hidden multipliers, so expected value is computed from published terms instead of hoped-for maximums

**Use when:** comparing programs on money and you need expected value rather than an advertised ceiling

**Avoid when:** the program pays a flat fee per accepted report and publishes no severity tiers or bonuses

## Procedure

1. Extract the full bounty table: severity bands, payout ranges, and which bands the program has actually paid historically.
2. Identify multipliers and modifiers such as quality bonuses, first-reporter rules and duplicate handling.
3. Model duplicate loss using the program's published duplicate rule and your own acceptance history, not optimism.
4. Compute expected value per severity band as payout times acceptance probability minus duplicate discount.
5. Compare programs on expected value per research hour, using effort estimates you recorded from past engagements.
6. Revisit the model when the program edits its table, since reward structures change more often than scope does.

## Signals

- The table shows a wide band whose lower bound is where nearly every real payment lands.
- A quality bonus exists but the program's report history shows it awarded rarely or never.
- Duplicate rules pay a finder's fee that makes racing other researchers the dominant strategy, which most hunters lose.
- Payout depends on severity scores the program assigns unilaterally after your report arrives.

## Patterns

**1. Value line**

```text
band=high payout=[500,3000] p-accept=0.35 p-dup=0.20 ev=892 per-hour=effort-6h ev-per-hour=149
```

**2. Modifier row**

```text
rule=first-reporter effect=-0.40-on-dup rule=quality-bonus effect=+0.15-observed-rare
```

**3. Model note**

```text
assumption=acceptance-from-own-history n=12 window=2026-h1 confidence=medium
```

## Pitfalls

- Modeling with the advertised maximum as if it were the typical payment, which inflates every comparison.
- Ignoring duplicate rules that gut payouts on popular asset classes where dozens of hunters work the same surface.
- Forgetting that severity is assigned by the program after submission, so payout is a post-hoc negotiation, not a lookup.
- Comparing across programs without normalizing for effort, so a low-paying fast program loses to a rich slow one.

## Done when

- Every candidate program has an expected value per research hour computed from published terms and your own rates.
- Duplicate and quality modifiers are modeled explicitly with the assumptions written next to the numbers.
- A refresh trigger is recorded for each bounty table you depend on.

## References

- [FIRST - Common Vulnerability Scoring System](https://www.first.org/cvss/)
- [CWE - weakness catalog](https://cwe.mitre.org/)
