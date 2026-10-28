---
name: scope-clause-interpretation
description: "Read a program's scope clauses as a contract rather than a mood, resolving each ambiguous in-scope claim into a testable asset list before you send a single request. Use when scope text contains words like reasonable, adjacent, or similar that expand or shrink what you may test"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [scope, program-selection, authorization]
---

# Scope Clause Interpretation

> Read a program's scope clauses as a contract rather than a mood, resolving each ambiguous in-scope claim into a testable asset list before you send a single request

**Use when:** scope text contains words like reasonable, adjacent, or similar that expand or shrink what you may test

**Avoid when:** the program publishes an exact hostname and endpoint list with no interpretive language at all

## Procedure

1. Copy every scope sentence verbatim into an interpretation worksheet so paraphrase never becomes the working definition.
2. Split each clause into the asset it names, the qualifier attached to it, and the conditions that void it.
3. Mark each clause as explicit, inferred or disputed, and treat only explicit entries as authorized without confirmation.
4. Write the narrowest reasonable reading and the widest plausible reading side by side for every ambiguous clause.
5. Send the narrow reading to the program as a confirmation question and wait for the answer before testing the gap.
6. Version the worksheet so a later scope edit shows exactly which interpretation changed and when.

## Signals

- A clause names a platform rather than a host, which means every subdomain claim needs its own decision.
- The words similar to or adjacent to appear next to an asset list, silently widening the boundary.
- A separate safety section contradicts the scope table, and whichever is narrower must govern your testing.
- Third-party owned assets sit inside scope, which shifts the authorization question onto a different party.

## Patterns

**1. Clause row**

```text
text='api.example.com and similar' kind=inferred narrow=api.example.com wide=*.example.com status=pending-confirmation
```

**2. Worksheet line**

```text
clause=2 asset=cdn-host qualifier='owned by program' conditions=excluded-if-third-party narrow=yes
```

**3. Confirmation ask**

```text
q=does 'similar' include staging.example.com? sent=2026-10-27 reply=awaiting program=alpha
```

## Pitfalls

- Treating the widest reading as safe because it yields more targets, when the narrow reading is the authorized one.
- Testing the gap while the confirmation email is still in flight, then arguing intent if a program objects.
- Interpreting scope from memory weeks later instead of from the versioned worksheet you already maintained.
- Ignoring expiry conditions, where a scope clause silently voids itself after a disclosure deadline passes.

## Done when

- Every scope clause has a narrow reading, a wide reading and an explicit-or-inferred classification.
- All disputed clauses have a confirmation question sent, and no testing has started on the disputed ground.
- The worksheet is versioned so future scope edits diff against a known baseline.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [OWASP - authorization and scope guidance](https://owasp.org/www-project-web-security-testing-guide/)
