---
name: retest-confirmation-tracking
description: "Track every fix through your own independent retest to confirmed-fixed, because a program's deployment note is a claim and your retest is the check. Use when a report is closed as resolved and you owe a confirmation or a not-yet-fixed reply"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [followup, verification, retest]
---

# Retest Confirmation Tracking

> Track every fix through your own independent retest to confirmed-fixed, because a program's deployment note is a claim and your retest is the check

**Use when:** a report is closed as resolved and you owe a confirmation or a not-yet-fixed reply

**Avoid when:** the program explicitly ends researcher involvement at fix deployment and accepts no retest

## Procedure

1. Record the close claim: what was fixed, on which version, and the date the program stated.
2. Wait for the fix to reach the environment you can actually reach, and note the version you tested.
3. Re-run your minimal reproduction verbatim from clean state rather than from memory.
4. Classify the result as fixed, partially-fixed, not-fixed or changed-behavior, with the evidence for each.
5. Reply with the retest outcome whether it passes or fails, since silence converts a partial fix into a closed success.
6. Update your finding record with the retest date, version and result so the closure is evidence-backed.

## Signals

- The close note says deployed but the version you can reach still behaves the old way.
- The original trigger no longer fires but a variant on the same path still does, which is partial, not fixed.
- You are tempted to confirm from the changelog rather than from a live retest.
- The retest used a stale session or cached state, so the result reflects your environment rather than theirs.

## Patterns

**1. Retest line**

```text
version=2.32.1 trigger=fires:no variant=/export/fires:yes verdict=partial reply=sent-2026-10-27
```

**2. Schedule note**

```text
close-claimed=2026-10-20 seen-live=2026-10-27 delay=7d reason=rollout-lag note=test-what-you-reach
```

**3. Retest record**

```text
finding=F-118 retest=pass date=2026-10-27 version=2.32.1 evidence=req-resp-pair-3 archived=yes
```

## Pitfalls

- Confirming from release notes instead of from a live reproduction, which may be wrong about your environment.
- Retesting without resetting, so leftover state masks the defect and you report a false pass.
- Going silent on a failed retest, letting the program count it as fixed.
- Retesting a partial fix as binary, either missing the remaining variant or refusing to credit real progress.

## Done when

- The retest ran verbatim from clean state against the reachable version with its evidence saved.
- The outcome is classified as fixed, partial, not-fixed or behavior-changed, and the program received it.
- The finding record carries retest date, version and result.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [OWASP - testing guidance for fix verification](https://owasp.org/www-project-web-security-testing-guide/)
