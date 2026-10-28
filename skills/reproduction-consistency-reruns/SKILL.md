---
name: reproduction-consistency-reruns
description: "Re-run a finished reproduction on a separate day, session and vantage point to catch day-one luck before triage does it for you and files it as not-reproducible. Use when a finding is complete and about to be submitted but has only ever been run once"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reproduction, evidence, quality]
---

# Reproduction Consistency Reruns

> Re-run a finished reproduction on a separate day, session and vantage point to catch day-one luck before triage does it for you and files it as not-reproducible

**Use when:** a finding is complete and about to be submitted but has only ever been run once

**Avoid when:** the defect has already been independently reproduced by a second party

## Procedure

1. Set the finding aside for a defined interval so accumulated state and assumptions lose their grip.
2. Re-run the full documented procedure from clean state, following only what is written, not what you remember.
3. Note every point where the written procedure was ambiguous, then fix the procedure rather than your memory.
4. Run the procedure from a second vantage point, different network or machine, to expose environment dependence.
5. Compare outcomes across runs and record consistency explicitly in the report.
6. If a run fails, treat the procedure as the suspect first and the defect as the second suspect.

## Signals

- The reproduction was written minutes after discovery, when every implicit step still felt obvious.
- Only one person has ever run it, which means unmeasured consistency rather than known consistency.
- The procedure mentions steps like repeat the earlier request, which references state that no longer exists.
- A rerun succeeds only because you know the trick, which is exactly what triage will not know.

## Patterns

**1. Rerun record**

```text
day=0 runs=2 fired=2 day=+2 runs=2 fired=2 vantage=second-network fired=yes consistency=4/4
```

**2. Ambiguity note**

```text
step=4 unclear='the earlier request' fix=specify-request-4471-with-id-replaced
```

**3. Variance line**

```text
vantage=home fired=yes vantage=mobile-lte fired=yes implication=no-network-dependence
```

## Pitfalls

- Re-running from memory instead of from the document, which silently tests your recall rather than the procedure.
- Treating a failed rerun as the defect disappearing instead of as an ambiguous instruction in the steps.
- Skipping the second vantage point, so an environment dependence survives into submission.
- Noting consistency in your head rather than in the report, leaving the claim invisible to triage.

## Done when

- The procedure has been re-run from written instructions on a later day with the outcome recorded.
- A second vantage point has been tested and the result noted.
- Every ambiguity found during rerun has been fixed in the procedure itself.

## References

- [OWASP - testing guidance for reliable test cases](https://owasp.org/www-project-web-security-testing-guide/)
- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
