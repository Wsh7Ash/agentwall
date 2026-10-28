---
name: program-relationship-maintenance
description: "Keep the working relationship with a program's triage team deliberate and professional across reports, because consistent, low-friction researchers get read carefully and paid fairly. Use when you submit repeatedly to the same program and want the working channel to stay productive"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [followup, communication, career]
---

# Program Relationship Maintenance

> Keep the working relationship with a program's triage team deliberate and professional across reports, because consistent, low-friction researchers get read carefully and paid fairly

**Use when:** you submit repeatedly to the same program and want the working channel to stay productive

**Avoid when:** you have filed a single report and expect no further contact

## Procedure

1. Respond professionally regardless of verdict, since tone in one exchange sets the tone for the next.
2. Reference prior reports when relevant, so patterns and context do not have to be re-explained each time.
3. Report genuine product issues you notice outside your findings through the proper channel, without bounty expectation.
4. Keep promises you made in threads, such as sending a capture or respecting a deadline, and do so visibly.
5. Thank triage staff specifically when they helped, which costs nothing and is remembered.
6. Track which contacts and channels have been responsive so future reports route to the path that works.

## Signals

- Triage replies to your reports faster than to the program's average, which is a asset worth maintaining.
- You have promised a follow-up capture in a thread and it has not yet been sent.
- A contact who handled your reports has gone quiet, and no alternate route is recorded.
- Feedback from triage keeps pointing at the same weakness in your submissions, which is free coaching.

## Patterns

**1. Channel note**

```text
contact=triage-a latency=2d reliability=high contact=platform latency=6d route=primary-and-backup
```

**2. Promise log**

```text
promised=send-capture-2 due=2026-10-28 sent=yes thread=F-119 keep-visible=yes
```

**3. Pattern feedback**

```text
theme=repro-steps-vague reports-affected=3 action=add-clarity-checklist-to-report-phase
```

## Pitfalls

- Going silent after a rejected report, which forfeits the relationship over a single verdict.
- Making thread promises you do not track, which quietly costs credibility with the people who read you.
- Using a personal channel for bounty disputes, mixing relationship management with leverage.
- Collecting responsive contacts without a backup, so one departure strands your routing.

## Done when

- Promises made in threads are tracked and visibly kept.
- Primary and backup contacts or channels are recorded for each active program.
- Recurring triage feedback has been converted into a change in your own report process.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [CISA - coordinated vulnerability disclosure guidance](https://www.cisa.gov/coordinated-vulnerability-disclosure-process)
