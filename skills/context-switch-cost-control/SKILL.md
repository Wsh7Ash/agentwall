---
name: context-switch-cost-control
description: "Protect deep research sessions from context switching by batching shallow work into declared windows, because recon and exploitation lose their thread faster than any other mode. Use when your sessions are repeatedly fragmented by triage replies, platform notifications and small errands"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [focus, queue, productivity]
---

# Context Switch Cost Control

> Protect deep research sessions from context switching by batching shallow work into declared windows, because recon and exploitation lose their thread faster than any other mode

**Use when:** your sessions are repeatedly fragmented by triage replies, platform notifications and small errands

**Avoid when:** your role is incident response where interruption is the job and batching is not possible

## Procedure

1. Identify every recurring interrupt source that touches a research session: alerts, chat, email and platform notifications.
2. Group all shallow work such as triage replies and ticket updates into fixed daily windows outside deep sessions.
3. Declare the deep session's single question before starting, so a switch away has a defined resumption point.
4. Leave a resumption note at every break, capturing state in one or two lines so restarting does not require replay.
5. Measure how often deep sessions were actually interrupted and what caused each break.
6. Tune the batching boundaries monthly, moving any interrupt source that still leaks into protected windows.

## Signals

- Restarting a session after a short interruption consumes far more of the block than the interruption itself.
- You cannot state the session's question from memory after returning from a break.
- Platform notifications arrive during exploitation work and pull you into triage you did not plan.
- Resumption notes are absent, so every return trip re-derives context from scratch.

## Patterns

**1. Batch window**

```text
deep=09:00-12:00 shallow-batch=16:00-16:45 sources=[platform,email,chat] exception=incident-only
```

**2. Resumption note**

```text
state=request-42-broken-at-authz step=next-replay-with-user-b-explicitly hypothesis=cache-serves-user-a
```

**3. Interrupt log**

```text
count=7 sources=platform=4 chat=2 chat=1 action=mute-platform-during-deep
```

## Pitfalls

- Batching shallow work into a window that overlaps your actual peak research hours.
- Writing no resumption note, then paying the full context rebuild cost at every return.
- Treating every notification as urgent when most platform traffic is routine and batchable.
- Over-scheduling batching so shallow work spills back into protected time anyway.

## Done when

- Deep windows are declared, shallow work is batched outside them, and sources are muted or deferred.
- Every break in a deep session leaves a resumption note sufficient to restart without replay.
- Interruption counts are tracked and the top source has an explicit containment action.

## References

- [OWASP - testing guidance for focused testing sessions](https://owasp.org/www-project-web-security-testing-guide/)
- [ISO 29147 - vulnerability disclosure for triage batching](https://www.iso.org/standard/72311.html)
