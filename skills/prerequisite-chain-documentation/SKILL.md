---
name: prerequisite-chain-documentation
description: "Document every precondition a defect depends on, in order, so triage can rebuild your exact starting position instead of guessing at what state the test assumed. Use when a defect only fires after a specific sequence of setup, roles, flags or data exists"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reproduction, evidence, documentation]
---

# Prerequisite Chain Documentation

> Document every precondition a defect depends on, in order, so triage can rebuild your exact starting position instead of guessing at what state the test assumed

**Use when:** a defect only fires after a specific sequence of setup, roles, flags or data exists

**Avoid when:** the defect fires on a default installation with no setup beyond an account

## Procedure

1. List every precondition: account roles, feature flags, prior actions, data rows and entitlement states.
2. Order the prerequisites so the chain can be executed top to bottom without improvisation.
3. Mark which prerequisites are default, obtainable through the product, or requiring privileged access.
4. State the time dependence: how long a precondition takes to establish and how long it remains true.
5. Verify the chain by following it literally from a fresh environment and noting where the instructions were ambiguous.
6. Attach the ordered chain to the report as its own section, separate from the trigger steps.

## Signals

- Your reproduction assumes two accounts in different roles without saying which actions created their state.
- A feature flag must be on and you never recorded how you turned it on or whether it defaults on.
- The defect requires data that accumulates over time, which changes who can reproduce it and when.
- Triage's first reply is always a request for the missing setup, which the chain would have pre-empted.

## Patterns

**1. Chain line**

```text
1=admin-account 2=invite-member 3=member-creates-order 4=admin-transfers-ownership 5=member-re-fetches
```

**2. Flag note**

```text
flag=new-checkout default=off how-enabled=admin-console time-to-enable=2m persists=until-redeploy
```

**3. Time dep**

```text
precondition=account-age>30d implication=triage-cannot-repro-today mitigation=seed-or-wait note=state-it
```

## Pitfalls

- Describing prerequisites as prose narrative, which forces triage to re-derive their order.
- Assuming a precondition is default when it was actually enabled during your own earlier testing.
- Omitting time-dependent preconditions, making the defect appear non-reproducible to everyone but you.
- Mixing prerequisites into the trigger steps so neither section can be followed independently.

## Done when

- Prerequisites are listed in executable order with their source: default, product-obtainable or privileged.
- Time dependence and persistence of each precondition is stated.
- The chain has been followed literally from a fresh environment with ambiguities fixed.

## References

- [OWASP - testing guidance for test case documentation](https://owasp.org/www-project-web-security-testing-guide/)
- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
