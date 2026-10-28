---
name: disclosure-timing-coordination
description: "Coordinate any public disclosure with the program's stated timeline and fix state, so publishing informs users without blindsiding a team still shipping the patch. Use when you intend to publish details and the program's policy sets conditions or dates for doing so"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [followup, disclosure, communication]
---

# Disclosure Timing Coordination

> Coordinate any public disclosure with the program's stated timeline and fix state, so publishing informs users without blindsiding a team still shipping the patch

**Use when:** you intend to publish details and the program's policy sets conditions or dates for doing so

**Avoid when:** the program prohibits publication entirely or you have no intention of publishing

## Procedure

1. Read the program's disclosure policy verbatim and record the conditions, delays and blackout periods it sets.
2. Confirm the fix state with the program before publishing anything, rather than inferring from a changelog.
3. Agree the date in writing if policy allows coordinated timing, and treat silence as not-yet-cleared.
4. Draft the public write-up to omit details that would enable abuse of unpatched surfaces.
5. Re-check the fix state on the publication date, since rollouts slip and dates silently stop being true.
6. Archive the cleared date, the state confirmed and the published version with the finding record.

## Signals

- Policy sets a fixed window after fix and you are approaching it without having confirmed the fix state.
- A partial fix has shipped while your write-up assumes the whole issue is closed.
- The publication date was agreed verbally and does not appear in the thread anywhere.
- Your draft includes reproduction detail for a surface you have not confirmed as patched.

## Patterns

**1. Coord line**

```text
policy=90d-after-fix fix-confirmed=2026-10-27 earliest-publish=2027-01-25 cleared-by=program-in-writing
```

**2. State check**

```text
surface=/api/v2 fixed=yes surface=export variant=still-open action=exclude-variant-from-write-up
```

**3. Disclosure archive**

```text
date=2026-10-27 state=confirmed version=2.32.1 policy-snapshot=archived next-check=publish-date
```

## Pitfalls

- Publishing on a remembered schedule instead of the policy's actual conditions.
- Assuming full fix when only the reported variant was closed, which advertises the remaining gap.
- Treating no reply as approval, which is how teams get blindsided by their own timeline.
- Skipping the final state check on publication day, when rollouts have usually moved.

## Done when

- Policy conditions are recorded with the fix state confirmed in writing before publication.
- The write-up excludes any surface not confirmed patched.
- The cleared date, confirmed state and published version are archived with the finding.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [CISA - coordinated vulnerability disclosure guidance](https://www.cisa.gov/coordinated-vulnerability-disclosure-process)
