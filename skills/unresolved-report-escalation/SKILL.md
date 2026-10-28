---
name: unresolved-report-escalation
description: "Escalate a stalled report along a defined path with a written summary and evidence attached, so aging tickets get a decision instead of drifting past every published response window. Use when a report has passed the program's stated response or resolution window with no movement"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [followup, escalation, communication]
---

# Unresolved Report Escalation

> Escalate a stalled report along a defined path with a written summary and evidence attached, so aging tickets get a decision instead of drifting past every published response window

**Use when:** a report has passed the program's stated response or resolution window with no movement

**Avoid when:** the report is inside its published window and triage has already responded recently

## Procedure

1. Confirm the report has actually exceeded the program's published window, citing the exact dates.
2. Assemble a short escalation summary: what was submitted, when, what was asked, what was answered, what is owed.
3. Route the escalation through the documented path first, such as the platform's escalation or tam contact.
4. State a specific requested outcome, whether a decision, a severity discussion or a status confirmation.
5. Escalate one level at a time, keeping each message factual and free of grievance.
6. Log the escalation and its result so your program health model reflects how the program handles aging work.

## Signals

- The program publishes a response time and your report has passed it twice over.
- Your last three messages in the thread have gone unanswered while the ticket stays open.
- You are drafting an escalation that reads as frustrated rather than as a request for a decision.
- No documented escalation path exists, which itself is a finding about the program's process.

## Patterns

**1. Escalate line**

```text
submitted=2026-09-12 window=14d last-reply=2026-10-02 owed=severity-decision route=platform-tam
```

**2. Summary block**

```text
submitted=9-12 asked=10-01 answered=10-02 owed=status note=three-lines-each-fact
```

**3. Level log**

```text
level=1=triage level=2=platform-tam date=2026-10-27 result=pending next=2026-11-03
```

## Pitfalls

- Escalating before confirming the program's own window had actually elapsed.
- Escalating in anger, which converts a process failure into a relationship problem you lose.
- Skipping the documented path and going public first, which forecloses the cooperative route.
- Not logging outcomes, so the health model never learns that this program ages reports.

## Done when

- The elapsed window is documented with dates and the escalation summarizes facts over grievance.
- Escalation followed the documented path with a specific requested outcome stated.
- The outcome is logged against the program's health record.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [CISA - coordinated vulnerability disclosure guidance](https://www.cisa.gov/coordinated-vulnerability-disclosure-process)
