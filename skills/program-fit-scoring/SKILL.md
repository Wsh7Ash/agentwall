---
name: program-fit-scoring
description: "Score every candidate program against your real skills, access and payout expectations before spending a research hour, so limited capacity flows to programs you can actually win in. Use when you are choosing which programs to add to this quarter's queue and research capacity is finite"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [program-selection, triage, planning]
---

# Program Fit Scoring

> Score every candidate program against your real skills, access and payout expectations before spending a research hour, so limited capacity flows to programs you can actually win in

**Use when:** you are choosing which programs to add to this quarter's queue and research capacity is finite

**Avoid when:** you are already engaged with one program and only need to decide what to test next inside it

## Procedure

1. List every program under consideration with its scope size, asset types, payout range and published response times.
2. Score your own fit per program: matching expertise, tooling you already own, and whether the assets are reachable from your position.
3. Weight payout against effort using your historical data, not the program's advertised maximum bounty.
4. Record the score with one sentence of reasoning so a later review can challenge the judgment instead of re-deriving it.
5. Rank programs and cut anything below your fit threshold, keeping the cut list with reasons rather than deleting it.
6. Re-score whenever a program changes scope, payout bands or response commitments, because fit is a moving property.

## Signals

- A program's advertised bounty ceiling sits far above what your historical acceptance rate earns on similar scope.
- Scope includes asset classes you have never tested and no tooling exists for them on your side.
- Published response times slip beyond two weeks on every report you have filed there historically.
- Two candidate programs score within a few points, which means the tie-break must be written down explicitly.

## Patterns

**1. Fit score row**

```text
program=alpha fit=0.82 exp=api authz tools=yes payout=mid resp=5d note=strong-match
program=beta  fit=0.41 exp=iot     tools=no   payout=high resp=21d note=no-access
```

**2. Weighting line**

```text
score = 0.4*expertise + 0.3*tooling + 0.2*payout-realism + 0.1*response-speed
```

**3. Cut record**

```text
cut=beta reason=unreachable-assets revisit-when=remote-access-granted owner=you
```

## Pitfalls

- Scoring against the advertised maximum payout when your own data says you realistically earn a fraction of it.
- Counting scope size as fit, which rewards programs so broad that you can never reach meaningful depth on any asset.
- Letting the score rot: a program that narrowed scope or cut payouts last month still sits at last quarter's rating.
- Skipping the written reasoning, so next quarter's review cannot tell a considered judgment from a mood.

## Done when

- Every candidate program carries a numeric fit score, one line of reasoning and a keep-or-cut decision.
- The ranked queue names the next program to research, and the cut list explains why each loser lost.
- A re-score trigger is recorded for each kept program so scope or payout changes force a fresh rating.

## References

- [CWE - weakness catalog for fit against program scope](https://cwe.mitre.org/)
- [FIRST - Common Vulnerability Scoring System](https://www.first.org/cvss/)
