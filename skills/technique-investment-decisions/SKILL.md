---
name: technique-investment-decisions
description: "Decide deliberately which techniques, tooling and study to invest in next, weighted by what your program mix actually rewards rather than by what the community is loudest about. Use when choosing between competing investments: new tooling, a new technique, or deeper study of one area"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [portfolio, skills, planning]
---

# Technique Investment Decisions

> Decide deliberately which techniques, tooling and study to invest in next, weighted by what your program mix actually rewards rather than by what the community is loudest about

**Use when:** choosing between competing investments: new tooling, a new technique, or deeper study of one area

**Avoid when:** an engagement deadline already dictates what must be learned this week

## Procedure

1. List candidate investments with what each would enable: which programs, which defect classes, which surfaces.
2. Weight each by the program mix you actually work in, since a technique nobody you target needs will not pay.
3. Estimate time-to-usable for each candidate, including the practice needed before it produces findings.
4. Check whether the investment complements strengths you already have or opens an area you avoid for other reasons.
5. Choose a bounded number of investments for the period and explicitly defer the rest with reasons.
6. Review the chosen investments against findings they enabled, and drop the ones that produced nothing.

## Signals

- A technique is popular in your feed but none of your active programs reward the defect class it targets.
- Time-to-usable for a candidate is long and you have no practice plan, which means it will never reach use.
- Investments accumulate quarter over quarter without any being evaluated or dropped.
- Every candidate targets a new area while your existing strengths go unexploited.

## Patterns

**1. Choice line**

```text
invest=graphql-depth enabled=2-active-programs time-to-usable=3-weeks weight=0.6 verdict=fund
```

**2. Defer record**

```text
candidate=wasm-reversal reason=no-matching-program revisit=when-mix-changes note=recorded-not-forgotten
```

**3. Outcome check**

```text
investment=fuzzing-setup findings-enabled=1 cost=2-weeks verdict=keep-or-drop next=review-2027-01
```

## Pitfalls

- Chasing techniques that trend rather than techniques your target programs reward.
- Funding too many investments at once, so none reaches the practice threshold where it pays.
- Never dropping an investment, which turns the list into a museum of abandoned intentions.
- Ignoring complementary strengths, always opening new areas while existing ones stay shallow.

## Done when

- Each candidate investment states what it enables and is weighted against your real program mix.
- A bounded funded set exists with explicitly deferred candidates and reasons.
- Each funded investment has an outcome review that decides keep or drop.

## References

- [CWE - weakness catalog for technique targeting](https://cwe.mitre.org/)
- [OWASP - testing guidance](https://owasp.org/www-project-web-security-testing-guide/)
