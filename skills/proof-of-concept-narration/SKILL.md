---
name: proof-of-concept-narration
description: "Narrate a proof of concept as a story with intent, action and observed result, so a reviewer follows why each request was sent instead of staring at an unexplained payload. Use when your PoC works but reads as a request dump with no explanation of what each part demonstrates"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reporting, poc, writing]
---

# Proof of Concept Narration

> Narrate a proof of concept as a story with intent, action and observed result, so a reviewer follows why each request was sent instead of staring at an unexplained payload

**Use when:** your PoC works but reads as a request dump with no explanation of what each part demonstrates

**Avoid when:** the program wants raw request-response pairs only and no narrative at all

## Procedure

1. State the goal of the PoC in one sentence: the specific claim it is designed to demonstrate.
2. Break the PoC into phases with a named purpose each: establish state, trigger, observe, confirm.
3. Explain the function of every non-obvious parameter so nothing looks like unexplained magic.
4. Annotate each response with what it proves relative to the goal stated at the top.
5. End with a verdict line that says plainly which claim the PoC did and did not establish.
6. Trim any step that does not advance the stated goal, since exploratory residue confuses the story.

## Signals

- A reviewer must reverse-engineer your intent from a sequence of unexplained requests.
- Payload fields are present with no note on why they take those values.
- The PoC demonstrates more than the claim, which invites scrutiny of parts you did not verify.
- Exploratory requests from the discovery session remain in the PoC as noise.

## Patterns

**1. Narrative line**

```text
phase=setup purpose=create-two-accounts phase=trigger purpose=swap-object-id phase=observe purpose=confirm-read
```

**2. Annotate note**

```text
response=200-with-invoice-body proves=member-a-read-member-b-object goal=tenant-isolation
```

**3. PoC verdict line**

```text
established=cross-tenant-read not-established=bulk-export-at-scale note=state-explicitly
```

## Pitfalls

- Shipping the raw request log from discovery as the PoC, which reads as noise rather than proof.
- Demonstrating extra capabilities you have not verified, widening the claim beyond your evidence.
- Leaving parameter values unexplained, which makes the whole PoC look like a copied recipe.
- Omitting the verdict line, so the reviewer must infer what you believe the PoC proved.

## Done when

- The PoC opens with a stated goal and closes with an explicit verdict of what it established.
- Every phase has a named purpose and every non-obvious parameter an explanation.
- No exploratory residue remains in the sequence.

## References

- [OWASP - testing guidance for proof of concept](https://owasp.org/www-project-web-security-testing-guide/)
- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
