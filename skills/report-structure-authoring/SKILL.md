---
name: report-structure-authoring
description: "Lay out a report so a tired triage engineer gets summary, impact, reproduction and evidence in that order, without hunting through prose for the four facts they need. Use when writing a submission that must be understood quickly by someone who has never seen the target"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reporting, writing, triage]
---

# Report Structure Authoring

> Lay out a report so a tired triage engineer gets summary, impact, reproduction and evidence in that order, without hunting through prose for the four facts they need

**Use when:** writing a submission that must be understood quickly by someone who has never seen the target

**Avoid when:** the platform enforces its own field structure that already dictates the ordering

## Procedure

1. Open with a two-sentence summary: what is wrong, on which asset, and what an attacker gains.
2. Follow with impact stated in the product's terms: data exposed, action performed, or money affected.
3. Place the reproduction as numbered steps with preconditions separated into their own short section.
4. Attach evidence inline next to the claim it supports rather than collecting everything at the end.
5. Close with severity rationale and any remediation direction you can justify from the evidence.
6. Cut every sentence that does not serve comprehension, because length costs triage time and your credibility.

## Signals

- A reviewer must scroll past narrative before reaching the reproduction steps they actually need.
- Impact is described in abstract security terms instead of in what the product's users lose.
- Evidence appears only in an appendix, forcing the reader to trust claims before seeing support.
- The report exceeds what the defect needs, which usually signals unorganized rather than thorough.

## Patterns

**1. Report outline**

```text
1=summary(2 sentences) 2=impact 3=preconditions 4=repro-steps 5=evidence-inline 6=severity-note
```

**2. Summary line**

```text
what=tenant-isolation-broken where=/api/v2/invoices attacker-gain=cross-tenant-read-of-billing
```

**3. Impact phrasing**

```text
user-visible=competitor-can-read-your-invoices-not=idaor-category-splat note=state-concrete-loss
```

## Pitfalls

- Burying the reproduction under background paragraphs that triage must skip to reach the facts.
- Describing impact as a category label instead of as the concrete loss a user or business suffers.
- Hoarding evidence at the end so the narrative asks for trust before it earns it.
- Padding to look thorough, which raises triage cost and lowers the chance of a careful read.

## Done when

- The first screen carries what is wrong, where, and what an attacker gains.
- Reproduction steps are numbered with preconditions in their own section.
- Every major claim has its supporting evidence attached beside it.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [CWE - weakness catalog for classification](https://cwe.mitre.org/)
