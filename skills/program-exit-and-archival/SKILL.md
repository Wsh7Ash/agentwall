---
name: program-exit-and-archival
description: "Close out a program that is winding down or going dark by resolving open reports, harvesting final outcomes and archiving the record before the platform deletes it all. Use when a program announces closure, stops responding entirely, or your engagement with it is ending"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [portfolio, followup, records]
---

# Program Exit and Archival

> Close out a program that is winding down or going dark by resolving open reports, harvesting final outcomes and archiving the record before the platform deletes it all

**Use when:** a program announces closure, stops responding entirely, or your engagement with it is ending

**Avoid when:** the program is active, responsive and simply slower than you would like

## Procedure

1. List every open, pending and recently closed report at the program and note its current state.
2. Push for final decisions on open reports while the program still exists, since closure usually ends that window.
3. Export or capture the outcomes you have: severities, bounty amounts, dates and the reports themselves.
4. Harvest what the record teaches, such as which programs paid, which classes they accepted, and how they treated you.
5. Archive the full evidence set locally with dates and identifiers intact for later reference or disputes.
6. Remove the program from active queue and capacity plans so it stops consuming planning attention.

## Signals

- Support and triage contacts have gone quiet across several weeks while the platform page still looks live.
- A closure announcement sets a final date after which reports and bounties will no longer be processed.
- Open reports have sat without movement longer than the program's own published response window.
- Your capacity plan still reserves hours for a program that can no longer accept or pay for findings.

## Patterns

**1. Exposure list**

```text
open=3 pending-decision=2 recently-paid=4 final-date=2026-12-01 days-left=35 action=chase-decisions
```

**2. Harvest line**

```text
paid-total=4200 accepted=7 rejected=2 dup=1 lesson=strong-on-authz weak-on-impact-evidence
```

**3. Archive record**

```text
captured=reports+replies+amounts format=markdown-and-json stored=local-dated-location note=ids-intact
```

## Pitfalls

- Letting open reports lapse unchased, accepting whatever default outcome the platform assigns.
- Trusting the platform to keep your history, when closure often precedes deletion of researcher data.
- Harvesting nothing, so the same program mistakes get repeated at the next one.
- Leaving the program in your capacity plan, which quietly wastes every planning session that follows.

## Done when

- Every open report has been chased for a decision or recorded as abandoned with the reason.
- Outcomes, amounts and lessons are harvested and the full evidence set is archived locally with dates.
- The program is removed from queue, capacity and scoring models so it stops shaping active plans.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [CISA - coordinated vulnerability disclosure guidance](https://www.cisa.gov/coordinated-vulnerability-disclosure-process)
