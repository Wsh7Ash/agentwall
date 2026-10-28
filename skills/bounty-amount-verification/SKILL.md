---
name: bounty-amount-verification
description: "Verify the awarded bounty against the program's published table and your argued severity, so a misapplied band is caught within the payout window rather than accepted silently. Use when a bounty is offered or paid and you have a severity rating you argued for in the report"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [followup, payout, verification]
---

# Bounty Amount Verification

> Verify the awarded bounty against the program's published table and your argued severity, so a misapplied band is caught within the payout window rather than accepted silently

**Use when:** a bounty is offered or paid and you have a severity rating you argued for in the report

**Avoid when:** the program pays a flat published amount with no severity bands or discretion

## Procedure

1. Pull the current published bounty table and note the band boundaries that applied at submission time.
2. Confirm the severity that was actually assigned, which may differ from the severity you argued.
3. Compute the expected amount from band and any modifiers such as quality bonuses or first-reporter rules.
4. Compare expectation against the offer, checking band, currency and any platform fee deductions.
5. Raise a discrepancy within the program's stated window with the table, band and calculation attached.
6. Log the final amount and any correction so your reward model uses settled numbers rather than offers.

## Signals

- The offer lands in a lower band than the assigned severity maps to on the published table.
- The program assigned a different severity than you argued without a message explaining the change.
- The table was edited between submission and payout, and the older, higher band applied when you filed.
- Platform fees or currency conversion quietly move the received amount away from the offered figure.

## Patterns

**1. Check line**

```text
severity=critical band=[3000,5000] offered=1500 assigned=high flag=band-mismatch action=ask-with-table-attached
```

**2. Timing note**

```text
submitted=2026-09-30 table-version=v3 table-at-submission=v2 band-then=[5000,8000] claim=use-v2
```

**3. Calc record**

```text
base=high-modifier=+15 quality first-reporter=no received=1150 expected=1150 verdict=correct
```

## Pitfalls

- Accepting the first offer without checking it against the band your assigned severity maps to.
- Checking against today's table when a different version applied at submission time.
- Missing the program's dispute window while you waited to feel certain about the discrepancy.
- Not logging the settled amount, so payout data stays populated with offers rather than outcomes.

## Done when

- The band applied matches the assigned severity under the table version in force at submission.
- Any discrepancy has been raised in-window with table, band and calculation attached.
- The settled amount is logged and feeds the reward model.

## References

- [FIRST - Common Vulnerability Scoring System](https://www.first.org/cvss/)
- [CWE - weakness catalog](https://cwe.mitre.org/)
