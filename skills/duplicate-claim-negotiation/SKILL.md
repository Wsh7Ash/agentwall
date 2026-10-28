---
name: duplicate-claim-negotiation
description: "Respond to a duplicate verdict by testing whether it is truly the same root cause, and by arguing the narrower case where your finding proves something the original did not. Use when a report is closed as a duplicate and your evidence suggests the overlap is partial"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [followup, duplicates, negotiation]
---

# Duplicate Claim Negotiation

> Respond to a duplicate verdict by testing whether it is truly the same root cause, and by arguing the narrower case where your finding proves something the original did not

**Use when:** a report is closed as a duplicate and your evidence suggests the overlap is partial

**Avoid when:** the original report clearly covers the identical root cause and impact on the identical asset

## Procedure

1. Obtain the original report's stated root cause and impact, or the platform's summary, before arguing anything.
2. Compare root causes first, since shared symptoms with distinct causes are usually not true duplicates.
3. Compare impact, asset and prerequisite differences item by item and write down which differences are real.
4. If overlap is genuine, concede the duplicate plainly and ask what partial credit or acknowledgment applies.
5. If overlap is partial, present the specific difference: different path, different prerequisite or different impact.
6. Record the verdict and the program's duplicate rule interpretation for future expectations.

## Signals

- The verdict cites only a shared symptom while your finding's root cause is on a different code path.
- The original required an administrator role and yours requires an ordinary account, which is a real difference.
- You feel certain the verdict is wrong but have not read what the original actually claimed.
- The program's duplicate rule promises partial credit that you have not asked for.

## Patterns

**1. Dup compare**

```text
root-cause=original:export-cache yours=query-filter impact=original:metadata yours:full-records verdict=partial-overlap
```

**2. Concede line**

```text
shared=root-cause accepted=yes ask=partial-credit-per-rule-4.2 note=do-not-litigate-a-clear-dup
```

**3. Argue note**

```text
difference=prereq admin-vs-free difference=path=/export-vs=/api claim=distinct-weakness evidence=two-captures
```

## Pitfalls

- Arguing duplicate status without ever learning what the original claimed.
- Treating shared symptoms as shared root causes in either direction, which weakens every future claim.
- Fighting a genuine duplicate, which costs goodwill worth more than the partial fee in question.
- Conceding without asking about partial credit the program's own rules may guarantee.

## Done when

- The comparison covers root cause, asset, prerequisite and impact with real differences written down.
- The verdict is either conceded with a partial-credit ask or contested with specific distinguishing evidence.
- The program's duplicate rule interpretation is recorded for future expectations.

## References

- [CWE - weakness catalog for root cause comparison](https://cwe.mitre.org/)
- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
