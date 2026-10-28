---
name: triage-response-handling
description: "Process a triage reply as a decision point rather than an email, classifying it into accept, clarify, duplicate or dispute with the next concrete action already named. Use when a program replies to a submitted report and the reply changes your planned next step"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [followup, triage, communication]
---

# Triage Response Handling

> Process a triage reply as a decision point rather than an email, classifying it into accept, clarify, duplicate or dispute with the next concrete action already named

**Use when:** a program replies to a submitted report and the reply changes your planned next step

**Avoid when:** the reply is a formality that requires no action beyond noting the status change

## Procedure

1. Read the reply fully before acting, since partial reads turn clarifications into premature defenses.
2. Classify it into one of accept, clarify, duplicate, downgrade or reject, and record the classification.
3. Identify the specific question or decision the reply contains, which is usually narrower than its tone.
4. Prepare a response that answers only what was asked, with evidence attached rather than restated.
5. Set the response deadline from the program's stated timeline and put it in your queue, not your memory.
6. Log the outcome against the program so your health and payout models absorb the real signal.

## Signals

- The reply contains a question but you started drafting a defense of severity instead of an answer.
- Classification is unclear, which means the reply itself is ambiguous and needs a clarifying question first.
- The program stated a response window and you have not recorded it anywhere.
- The reply's tone suggests frustration, which is information about their triage load rather than about your report.

## Patterns

**1. Classify line**

```text
reply=clarify question=which-account-created-the-order next=send-account-ids deadline=2026-10-30
```

**2. Answer note**

```text
asked=one-thing answered=one-thing evidence=req-resp-pair-attached digression=none
```

**3. Log record**

```text
program=alpha outcome=clarify-round-2 latency=3d implication=triage-thorough-not-slow
```

## Pitfalls

- Responding to tone instead of to the actual question, which spends the exchange on friction.
- Answering every implied question in the reply, which multiplies the number of things that can be wrong.
- Letting a deadline live only in your inbox, where it expires unseen.
- Skipping the outcome log, so program-level patterns stay invisible across dozens of reports.

## Done when

- The reply is classified, its concrete ask is answered with attached evidence, and the deadline is queued.
- The outcome and latency are logged against the program.
- Any counter-position needed has been drafted from evidence rather than from the reply's tone.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [CISA - coordinated vulnerability disclosure guidance](https://www.cisa.gov/coordinated-vulnerability-disclosure-process)
