---
name: reporting-channel-setup
description: "Confirm and record the authorized reporting path, contacts and encryption options before testing, so a real finding lands in the right inbox on hour one instead of being discovered later. Use when joining a program or onboarding a new target where reporting details are scattered across pages"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reporting, program-selection, setup]
---

# Reporting Channel Setup

> Confirm and record the authorized reporting path, contacts and encryption options before testing, so a real finding lands in the right inbox on hour one instead of being discovered later

**Use when:** joining a program or onboarding a new target where reporting details are scattered across pages

**Avoid when:** the program provides a single obvious reporting form and you have already used it successfully

## Procedure

1. Find every reporting channel the program offers: form, email, encrypted mail, bug bounty platform ticket and security text.
2. Verify each channel by sending a non-sensitive pre-engagement note and confirming it reaches a human, not an autoresponder.
3. Record which channel carries which guarantee, since platform tickets usually have SLAs that plain email lacks.
4. Note escalation contacts and what justifies using them, such as a report aging past the published response time.
5. Store encryption keys or fingerprints the program publishes so sensitive evidence can be sent confidentially.
6. Re-verify the channels when the program restructures, because a stale contact address silently drops real findings.

## Signals

- Two channels claim to be official and route to different teams with different response times.
- The published security email bounces or auto-replies with an unmonitored notice.
- Encryption keys are published but no fingerprint is offered, leaving authenticity unverifiable.
- The platform ticket form is the only channel with a response SLA, making it the default rather than the fallback.

## Patterns

**1. Channel table**

```text
channel=platform-ticket sla=5d status=verified-2026-10-27 channel=email sla=none status=no-reply-yet
```

**2. Probe note**

```text
kind=pre-engagement-note purpose=deliverability result=human-reply latency=2d
```

**3. Escalation rule**

```text
trigger=first-response>14d action=escalate-to contact=platform-tam note=document-evidence
```

## Pitfalls

- Discovering the correct channel only after you hold a critical finding and time already matters.
- Sending evidence over a channel with no confidentiality guarantee when the program published an encrypted option.
- Recording a contact person by name with no backup, so a team change leaves you without any path.
- Skipping deliverability verification, which turns an unmonitored address into a silent black hole.

## Done when

- Every reporting channel is recorded with its owner, guarantee and last verification date.
- At least one channel has been verified end to end with a human reply.
- An escalation trigger is written down with the contact to use when the primary path stalls.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [CISA - coordinated vulnerability disclosure guidance](https://www.cisa.gov/coordinated-vulnerability-disclosure-process)
