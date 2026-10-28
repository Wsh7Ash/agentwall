---
name: research-timeboxing
description: "Bound every investigation with a declared time box and a pre-committed exit condition, so low-yield threads stop consuming the week at the moment they stop paying. Use when a line of investigation has no natural stopping point and sessions keep overrunning"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [timeboxing, queue, focus]
---

# Research Timeboxing

> Bound every investigation with a declared time box and a pre-committed exit condition, so low-yield threads stop consuming the week at the moment they stop paying

**Use when:** a line of investigation has no natural stopping point and sessions keep overrunning

**Avoid when:** the work is a committed deliverable with an external deadline that already sets the boundary

## Procedure

1. Declare the box before starting: hours available, the hypothesis being tested, and the observation that would end it.
2. Write the exit condition in advance so it cannot be renegotiated with yourself mid-session when you are invested.
3. Track elapsed time against the box at natural checkpoints rather than only at the end.
4. Stop at the box and record what was learned, what remains unknown, and whether the next box is justified.
5. Re-queue the remainder as a new item with its own score, so continuation must earn its place again.
6. Review boxes that were extended repeatedly, since chronic extension means the box, not the work, is wrong.

## Signals

- You keep extending the box to finish a thread that is close to something, three sessions in a row.
- The original hypothesis has been quietly replaced by a more interesting but less valuable question.
- Nothing testable has been produced recently, only collection of more information about the same surface.
- Other queued items with higher value per hour have gone unstarted because this box keeps expanding.

## Patterns

**1. Box line**

```text
hypothesis=hidden-param-on-search box=3h exit=no-new-params result=0-found ended=3h next=drop-or-requeue
```

**2. Extension log**

```text
week=42 boxes=3 extended=2 reason=chasing-one-param implication=box-or-hypothesis-is-wrong
```

**3. Requeue note**

```text
carried=item-11 score=110 est=deep first-action=resume-with-capture-diff-hypothesis
```

## Pitfalls

- Setting the exit condition after the session has begun, which lets attachment rewrite the stopping rule.
- Extending boxes to feel finished, converting a bounded experiment into an unbounded obligation.
- Stopping at the box without recording the outcome, so the next session repeats discovery work.
- Using timeboxing to abandon promising work prematurely when the evidence actually supports one more box.

## Done when

- Every active investigation has a declared box, a pre-written exit condition and a recorded outcome.
- Extensions are logged with reasons and reviewed for patterns.
- Unfinished work re-enters the queue with a fresh score instead of resuming by default.

## References

- [OWASP - testing guidance for time-bounded testing](https://owasp.org/www-project-web-security-testing-guide/)
- [CWE - weakness catalog](https://cwe.mitre.org/)
