---
name: clarification-loop-management
description: "Keep clarification rounds short and bounded by answering the whole question each round, tracking open asks on both sides, and escalating when a loop stops converging. Use when a report is in its second or third round of questions and answers with no resolution in sight"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [followup, communication, triage]
---

# Clarification Loop Management

> Keep clarification rounds short and bounded by answering the whole question each round, tracking open asks on both sides, and escalating when a loop stops converging

**Use when:** a report is in its second or third round of questions and answers with no resolution in sight

**Avoid when:** the first round of clarification has just arrived and is straightforward

## Procedure

1. Track every open question on both sides in one list, so nothing is answered twice or dropped.
2. Answer all of a round's questions in a single reply rather than dribbling responses across days.
3. For each answer, attach the evidence directly instead of referencing an attachment from an earlier round.
4. Detect when answers are being requested repeatedly in different words, which means your last answer did not land.
5. Summarize the state after each round in two lines so both sides share one picture of where the loop stands.
6. Declare the loop stalled after a set number of rounds with no progress, and name the escalation path.

## Signals

- You have been asked the same question twice with different phrasing, which means the earlier answer failed.
- Open questions exist in two places, an email thread and your notes, and they no longer match.
- Rounds are stretching longer because each reply waits on a fresh capture you could have batched.
- Three rounds have passed with no movement toward a decision, which is the definition of stalled.

## Patterns

**1. Open-ask table**

```text
their-open=1:which-role theirs-answered=2 our-open=1:severity-basis our-answered=0 round=3
```

**2. Repeat flag**

```text
q-round-1=show-steps q-round-3=show-how-you-got-there verdict=same-ask action=attach-full-sequence
```

**3. Stall rule**

```text
rounds-without-decision=3 action=summarize-and-request-deadline escalation=platform-tam note=state-in-thread
```

## Pitfalls

- Replying incrementally, which stretches a three-day loop into three weeks of latency.
- Answering in prose when a capture would settle the question immediately.
- Losing track of your own open question, so your side of the loop silently closes unattended.
- Letting a stalled loop drift instead of declaring it stalled, which forfeits the escalation window.

## Done when

- Open questions on both sides are tracked in one place with each round's answers and evidence.
- Repeats are recognized as failed answers and addressed with stronger evidence.
- A stall has been declared with an escalation action if no decision arrives.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [CISA - coordinated vulnerability disclosure guidance](https://www.cisa.gov/coordinated-vulnerability-disclosure-process)
