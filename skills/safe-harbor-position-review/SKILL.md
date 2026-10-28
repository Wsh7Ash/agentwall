---
name: safe-harbor-position-review
description: "Establish in writing what protection the program actually grants researchers before testing begins, so authorization, liability and exit terms are known rather than assumed. Use when joining a new program whose policy page makes promises you have not verified against its actual terms"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [authorization, program-selection, policy]
---

# Safe Harbor Position Review

> Establish in writing what protection the program actually grants researchers before testing begins, so authorization, liability and exit terms are known rather than assumed

**Use when:** joining a new program whose policy page makes promises you have not verified against its actual terms

**Avoid when:** you already hold a signed testing agreement reviewed by counsel for this specific engagement

## Procedure

1. Locate the program's safe harbor statement, terms of service and any separate testing addendum, and archive dated copies.
2. Record exactly which actions are protected: scanning, exploitation, data access, social engineering and physical testing.
3. Note the exclusions, because a safe harbor clause that omits data access protects far less than its headline suggests.
4. Check the withdrawal clause and what event ends your authorization, such as a policy edit or a reported dispute.
5. Write a one-paragraph position summary stating what you may do, what you may not, and who confirmed it.
6. Re-read the archived copies whenever the program updates its policy, since protection can be narrowed without notice.

## Signals

- The policy promises safe harbor but the terms of service contain a contradictory acceptance section.
- Protection is conditioned on following a scope definition that the program can edit at any time.
- No named contact or legal entity appears anywhere, so nobody can confirm the promise if it is later disputed.
- The withdrawal clause is silent, which usually means authorization ends whenever the program decides it does.

## Patterns

**1. Position line**

```text
program=alpha protected=[scan,exploit] excluded=[data-access,social] confirmed-by=policy-page dated=2026-10-27
```

**2. Conflict flag**

```text
source=policy-page claim='authorized research' source=terms claim='no reverse engineering' verdict=narrower-wins
```

**3. Archive record**

```text
url=.../policy.html snapshot=2026-10-27 hash=sha256:9f2c... next-review=policy-change
```

## Pitfalls

- Accepting a marketing headline as legal protection when the binding terms say something narrower.
- Storing no dated copy, leaving you unable to prove what the policy promised on the day you tested.
- Assuming safe harbor covers data access because it covers scanning, when the two are separately excluded.
- Starting testing while a policy conflict is unresolved, which forfeits the argument that you acted in good faith.

## Done when

- Dated copies of every governing document are archived and a position summary states the protected actions.
- Every conflict between documents has been resolved to the narrower reading and recorded.
- A review trigger exists so a policy edit forces a fresh position summary before further testing.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [CISA - coordinated vulnerability disclosure guidance](https://www.cisa.gov/coordinated-vulnerability-disclosure-process)
