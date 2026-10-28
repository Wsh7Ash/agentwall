---
name: tooling-readiness-checklist
description: "Verify your tools, wordlists, credentials and environments before a session starts, so the time box is spent testing rather than repairing broken setup halfway through. Use when a queued session depends on tooling that has not been exercised since the last time you used it"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [tooling, queue, setup]
---

# Tooling Readiness Checklist

> Verify your tools, wordlists, credentials and environments before a session starts, so the time box is spent testing rather than repairing broken setup halfway through

**Use when:** a queued session depends on tooling that has not been exercised since the last time you used it

**Avoid when:** the session is pure passive analysis using a browser and notes you already verified this morning

## Procedure

1. List the concrete tooling each queued item requires: scanners, wordlists, accounts, proxies and capture paths.
2. Exercise each dependency once with a trivial known-good case before the session begins.
3. Confirm credentials and tokens still work and expire far enough out to cover the session.
4. Verify wordlists and payloads are present, current and sized for the box rather than a full overnight run.
5. Record the exact versions and configs used so a result can be reproduced or a failure explained.
6. Update the checklist whenever a session fails for a tooling reason, because each failure is a missing gate.

## Signals

- A tool has not been run since an upgrade that changed its flags, output format or default behavior.
- Credentials expire mid-session and the failure presents as strange application behavior rather than an auth error.
- The chosen wordlist is the full-size one, which will not finish inside the declared time box.
- Setup problems consume the first third of every session and the pattern has repeated for weeks.

## Patterns

**1. Ready line**

```text
item=param-discovery tool=crawler ver=1.8 wordlist=discovery-2k est-runtime=9m creds=valid-to-2026-11-30
```

**2. Smoke test**

```text
dependency=proxy result=pass dependency=token result=fail action=refresh-before-session
```

**3. Failure log**

```text
date=2026-10-20 cause=stale-flag-after-upgrade cost=40m fix=add-version-gate-to-checklist
```

## Pitfalls

- Skipping the smoke test because the tool worked last month, which is precisely when drift happens.
- Testing credentials by eye rather than by a live authenticated request that proves the session will work.
- Bringing an oversized wordlist to a one-hour box, then blaming the environment when it does not finish.
- Fixing tooling failures ad hoc without adding the gate, so the same failure recurs next month.

## Done when

- Every dependency for the queued item has been exercised once and passed a known-good case.
- Credentials, wordlists and versions are recorded with expiry inside the session window.
- Each historical tooling failure has produced a checklist gate that would have caught it.

## References

- [OWASP - testing guidance for tooling setup](https://owasp.org/www-project-web-security-testing-guide/)
- [CWE - weakness catalog](https://cwe.mitre.org/)
