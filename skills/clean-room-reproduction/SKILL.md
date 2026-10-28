---
name: clean-room-reproduction
description: "Reproduce a finding from a fresh state with no residue from your own testing, so the observation is provably caused by the defect rather than by your setup. Use when a finding must be confirmed before reporting or after your environment has been heavily mutated"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reproduction, evidence, validation]
---

# Clean Room Reproduction

> Reproduce a finding from a fresh state with no residue from your own testing, so the observation is provably caused by the defect rather than by your setup

**Use when:** a finding must be confirmed before reporting or after your environment has been heavily mutated

**Avoid when:** the behavior is already reproducible by a second person on their own untouched environment

## Procedure

1. Reset to a known baseline: new session, default settings, no leftover state from the earlier exploration.
2. Perform only the documented steps in order, without improvising extra requests between them.
3. Capture each request and response in sequence so the chain can be replayed and inspected by someone else.
4. Confirm the defect appears with exactly the documented inputs and no hidden precondition you forgot to record.
5. Repeat the sequence a second time from reset to confirm it is deterministic rather than incidental.
6. Record any precondition that turned out to be required, since an undocumented precondition invalidates the repro.

## Signals

- The defect vanishes when you replay from a fresh state, which means an earlier mutation was a hidden cause.
- Reproduction succeeds only with a cookie, header or flag your earlier testing had left behind.
- A second run differs from the first, pointing at race, randomness or server-side drift rather than a stable defect.
- The steps only work when you skip a step you assumed was irrelevant but which actually mattered.

## Patterns

**1. Clean run**

```text
state=fresh session=empty cookie=none steps=1-5 result=defect-reproduced determinism=2/2-runs
```

**2. Residue flag**

```text
precondition=stale-flag-from-earlier-test visible-to=only-you fix=reset-before-repro
```

**3. Sequence log**

```text
step=3 action=POST /orders status=200 step=4 action=GET /orders/other-user status=200 leak=yes
```

## Pitfalls

- Reproducing with state your own earlier testing created, which produces a finding nobody else can confirm.
- Skipping the second run, so a one-off race presents as a reliable defect and embarrasses you in triage.
- Editing steps between runs, which makes the two runs incomparable rather than confirming determinism.
- Omitting a precondition you did not realize mattered, leaving triage unable to reproduce at all.

## Done when

- The defect reproduces from a documented fresh state with every precondition written down.
- Two consecutive clean runs produce the same observation.
- The request-response chain is captured in replayable order.

## References

- [OWASP - testing guidance for reliable reproduction](https://owasp.org/www-project-web-security-testing-guide/)
- [CWE - weakness catalog](https://cwe.mitre.org/)
