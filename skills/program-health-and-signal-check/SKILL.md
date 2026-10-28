---
name: program-health-and-signal-check
description: "Vet a program's operational health from public signals before investing research time, because a broken triage pipeline turns valid findings into unpaid, unanswered tickets. Use when a program looks attractive on scope and payout but you have never filed a report with them"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [program-selection, triage, signals]
---

# Program Health and Signal Check

> Vet a program's operational health from public signals before investing research time, because a broken triage pipeline turns valid findings into unpaid, unanswered tickets

**Use when:** a program looks attractive on scope and payout but you have never filed a report with them

**Avoid when:** you already have several accepted reports and direct triage contact at the program

## Procedure

1. Read recent public disclosure threads for the program and note time-to-first-response and time-to-fix distributions.
2. Check whether the program answers scope questions at all, since silence during pre-sales predicts silence during triage.
3. Look for signs of churn: repeated triage contacts, policy rewrites, or bounty table changes within a few months.
4. Verify that accepted reports actually result in fixes, by matching disclosures to released patch notes or version bumps.
5. Weigh positive signals such as published statistics and researcher testimonials against the negative evidence you found.
6. Record a health verdict with the two or three observations that drove it, so a later recheck compares like with like.

## Signals

- Public reports from the program show first responses measured in weeks rather than days.
- Scope questions sent before joining went unanswered, which is the cheapest possible health probe.
- The program has rewritten its policy twice this year, suggesting triage process is still in flux.
- Accepted disclosures cluster without corresponding fixes, hinting that acceptance means acknowledgment, not repair.

## Patterns

**1. Health line**

```text
program=alpha first-response=4d median-fix=18d policy-edits=2/12mo verdict=proceed-with-caution
```

**2. Probe record**

```text
probe=scope-question sent=2026-10-20 reply=none age=7d interpretation=low-engagement
```

**3. Fix correlation**

```text
disclosed=9 patched=4 ratio=0.44 window=2y note=verify-against-release-notes
```

## Pitfalls

- Reading testimonials published on the program's own page as independent evidence of good triage.
- Ignoring small-sample noise where three slow reports out of four total decide your entire verdict.
- Skipping the probe question entirely and discovering the silence only after you have filed your own report.
- Treating a healthy program as permanently healthy, since triage teams churn faster than policies do.

## Done when

- A health verdict is recorded with the specific observations behind it and the date of the check.
- A pre-join probe has been sent and its response or silence is logged as evidence.
- A recheck interval is set so the verdict cannot silently outlive its evidence.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [CISA - coordinated vulnerability disclosure guidance](https://www.cisa.gov/coordinated-vulnerability-disclosure-process)
