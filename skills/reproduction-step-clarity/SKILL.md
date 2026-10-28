---
name: reproduction-step-clarity
description: "Write reproduction steps that a stranger can execute verbatim, with exact values, exact order and no pronouns whose antecedent lives three lines above. Use when your current steps contain words like it, then, or the same request that force re-reading"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reporting, reproduction, writing]
---

# Reproduction Step Clarity

> Write reproduction steps that a stranger can execute verbatim, with exact values, exact order and no pronouns whose antecedent lives three lines above

**Use when:** your current steps contain words like it, then, or the same request that force re-reading

**Avoid when:** the platform's step field enforces a format you cannot deviate from

## Procedure

1. Replace every vague noun with the literal endpoint, field name, identifier or button label.
2. Number the steps and make each one a single action with a single observable result.
3. Move all assumptions about state into preconditions rather than leaving them implied between steps.
4. Substitute real example values for ids, emails and tokens, using obviously fake but well-formed data.
5. Read the steps as someone who has never seen the product and mark every place you had to guess.
6. Have a second person follow the steps cold if any is available, and fix whatever they stumble on.

## Signals

- A step says repeat the earlier request, whose referent is not on the same screen.
- Ids appear as your own session's values with no indication of which must be replaced.
- Steps assume a logged-in role that is never stated as a precondition.
- You cannot read the steps aloud without hesitating, which means a triage reader will stall too.

## Patterns

**1. Step line**

```text
4=as member-b send GET /api/v2/invoices/INV-9921 expect=403 got=200 with-cookie=session-b
```

**2. Value note**

```text
value=INV-9921 owner=user-b role-of-actor=member-a replace-rule=substitute-your-own-pair
```

**3. Vague flag**

```text
found='then check the result' fix=split-into-4a-action-4b-observable-result
```

## Pitfalls

- Using your own live identifiers without marking which ones the reader must swap out.
- Leaving role assumptions implicit, so the reader's first attempt uses the wrong account.
- Grouping two actions into one step, which makes a failure at the second action undiagnosable.
- Editing for brevity until an instruction becomes ambiguous, trading clarity for length you did not need to save.

## Done when

- Every step is one action with one observable result and literal values.
- All state assumptions live in a preconditions section.
- A cold reader would not need to guess at any referent, role or value.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [OWASP - testing guidance for test documentation](https://owasp.org/www-project-web-security-testing-guide/)
