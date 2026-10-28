---
name: acceptance-rate-review
description: "Break down your acceptance rate by program, defect class and report quality so a falling number identifies which lever to pull instead of just feeling discouraging. Use when acceptance is dropping or sitting below what you expect and the aggregate number explains nothing"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [portfolio, metrics, triage]
---

# Acceptance Rate Review

> Break down your acceptance rate by program, defect class and report quality so a falling number identifies which lever to pull instead of just feeling discouraging

**Use when:** acceptance is dropping or sitting below what you expect and the aggregate number explains nothing

**Avoid when:** the sample is a handful of reports, where breakdowns are noise rather than signal

## Procedure

1. Segment acceptance by program first, because one difficult program can drag the aggregate on its own.
2. Segment the remainder by defect class to see whether a class you favor is being rejected or downgraded often.
3. Segment by report quality signals you can observe: rounds of clarification, retest requests, evidence completeness.
4. Read each segment's rejection reasons verbatim rather than counting them, since reasons encode the fix.
5. Identify the single largest loss bucket and design one change to your process aimed at it.
6. Re-measure after the change over a set number of reports, so the experiment has a defined endpoint.

## Signals

- Rejections cluster in one program while others accept consistently, which localizes the problem.
- Clarification rounds per report are rising, which flags evidence gaps before they become rejections.
- A defect class you enjoy is rejected at twice the rate of the others, which is a targeting problem.
- Rejection reasons are summarized in your head but never read verbatim, so the actual fix stays unknown.

## Patterns

**1. Segment table**

```text
program=alpha acc=0.75 program=beta acc=0.33 class=information-disclosure acc=0.4 class=authz acc=0.8
```

**2. Reason read**

```text
reasons=[needs-more-impact-evidence x5, out-of-scope x1] dominant=impact-evidence action=quantify-impact
```

**3. Experiment**

```text
change=impact-quantification-checklist n=10-reports start=2026-11-01 endpoint=2026-12-01
```

## Pitfalls

- Reading the aggregate rate, which localizes nothing and fixes nothing.
- Counting rejection reasons without reading them, so the dominant reason never teaches you anything.
- Concluding you are worse at a defect class when the class simply attracts tougher programs.
- Changing five things at once, which makes the re-measurement uninterpretable.

## Done when

- Acceptance is segmented by program, class and quality signal with verbatim reasons read.
- One largest loss bucket is named with a single targeted process change aimed at it.
- The experiment has a defined report count or date for re-measurement.

## References

- [CWE - weakness catalog for class-level analysis](https://cwe.mitre.org/)
- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
