---
name: hypothesis-backlog-triage
description: "Run a recurring triage over your idea backlog so hypotheses are ranked, merged, split or killed on evidence rather than surviving indefinitely on the hope that they are promising. Use when the backlog has grown past what you can hold in your head and duplicates are starting to appear"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [queue, triage, backlog]
---

# Hypothesis Backlog Triage

> Run a recurring triage over your idea backlog so hypotheses are ranked, merged, split or killed on evidence rather than surviving indefinitely on the hope that they are promising

**Use when:** the backlog has grown past what you can hold in your head and duplicates are starting to appear

**Avoid when:** the backlog holds fewer than a dozen items and you already know every entry's status

## Procedure

1. Dump every backlog item with its creation date, current score and the last evidence attached to it.
2. Merge items that describe the same underlying weakness from different angles, keeping the strongest framing.
3. Split items that bundle several independent tests, because a compound item can neither be started nor finished.
4. Kill items whose assumption has been falsified or whose target no longer exists, recording why each died.
5. Re-score survivors against fresh information such as new scope, new tooling or newly observed behavior.
6. Archive killed items instead of deleting them so future rounds do not resubmit the same dead idea.

## Signals

- Two backlog entries would be satisfied by the same single test, which means one is pure duplication.
- An item has not moved in several triages, which usually marks it as blocked, unclear or quietly disowned.
- New information has falsified an item's core assumption but the item still sits in the ranked list.
- Items are phrased as goals like check for IDOR rather than as testable hypotheses with a predicted observation.

## Patterns

**1. Merge record**

```text
kept=idor-on-orders-absorbed=ids-in-invoices reason=same-weakness-class evidence=one-test-covers-both
```

**2. Split record**

```text
was=check-authz-now=authz-object-level + authz-function-level reason=two-observable-outcomes
```

**3. Kill record**

```text
item=legacy-soap-endpoint reason=endpoint-retired-2026-09 killed=2026-10-27 archived=yes
```

## Pitfalls

- Merging items whose tests differ subtly, which quietly deletes a coverage angle you meant to keep.
- Killing the wrong side of a duplicate pair by keeping the newer phrasing instead of the better-evidenced one.
- Leaving falsified assumptions in the backlog because the idea once felt promising.
- Running triage without archiving, so the same dead idea returns every cycle and trust in the backlog decays.

## Done when

- Every item is ranked, merged, split or killed with the reason and date recorded.
- No two remaining items would be satisfied by the same single test.
- Killed items are archived with falsified assumptions noted for future reference.

## References

- [CWE - weakness catalog for hypothesis classes](https://cwe.mitre.org/)
- [OWASP - testing guidance](https://owasp.org/www-project-web-security-testing-guide/)
