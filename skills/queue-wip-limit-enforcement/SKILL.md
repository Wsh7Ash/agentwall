---
name: queue-wip-limit-enforcement
description: "Cap how many investigations are in flight at once and finish before starting, because work in progress is what turns a full queue into zero shipped findings. Use when many sessions are started and few reports are completed, with several half-finished threads open"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [queue, wip, focus]
---

# Queue WIP Limit Enforcement

> Cap how many investigations are in flight at once and finish before starting, because work in progress is what turns a full queue into zero shipped findings

**Use when:** many sessions are started and few reports are completed, with several half-finished threads open

**Avoid when:** you deliberately run one exploratory and one confirmatory thread in parallel by design

## Procedure

1. Set a small explicit work-in-progress limit, usually two or three active investigations at most.
2. List everything currently in flight and mark which items are genuinely blocked versus merely paused.
3. Finish or consciously stop blocked items before opening new ones, because starting is the cheap and addictive part.
4. Route new ideas into the backlog instead of the active list, keeping the backlog as the only admission point.
5. Review the limit when completed findings per month drop, since in-flight count is the first lever to pull.
6. Record items you were forced to stop so unfinished work re-enters the queue with evidence, not just intention.

## Signals

- Five investigations are open and none has produced a reportable observation in the current week.
- New ideas are being started directly instead of entering the backlog, which bypasses all ranking.
- Paused items are indistinguishable from blocked items, so nothing gets a real finish decision.
- Completion rate falls while session count stays flat, which is the signature of excessive in-flight work.

## Patterns

**1. Wip line**

```text
limit=3 active=3 open-ideas=6 routed-to=backlog=yes completed-this-month=4
```

**2. Stop record**

```text
item=graphql-depth status=stopped reason=no-auth'd-env next-action=requeue-when-env-arrives
```

**3. Blocked flag**

```text
item=waf-bypass state=blocked-on=credentials unblock-date=none age=12d decision=drop-or-ask
```

## Pitfalls

- Setting a limit and then opening emergencies that bypass it every single week, which makes the limit decorative.
- Counting blocked items as active work, so the real in-flight load is hidden by things you cannot move.
- Stopping items without recording their state, guaranteeing expensive re-discovery when they resume.
- Raising the limit during a productive streak, then wondering why throughput collapses a month later.

## Done when

- In-flight count is at or below the declared limit and every open item is finished, blocked or re-queued.
- New ideas enter only through the backlog with ranking applied.
- Stopped items carry a written state sufficient to resume without replaying discovery.

## References

- [OWASP - testing guidance for coverage and completion](https://owasp.org/www-project-web-security-testing-guide/)
- [CWE - weakness catalog](https://cwe.mitre.org/)
