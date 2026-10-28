---
name: baseline-trigger-comparison
description: "Capture a correct-behavior baseline alongside the defective response so the difference is the evidence, eliminating arguments about what the system should have returned. Use when a finding rests on an unexpected response whose wrongness is not self-evident"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reproduction, evidence, validation]
---

# Baseline Trigger Comparison

> Capture a correct-behavior baseline alongside the defective response so the difference is the evidence, eliminating arguments about what the system should have returned

**Use when:** a finding rests on an unexpected response whose wrongness is not self-evident

**Avoid when:** the response is unambiguously invalid, such as another user's plaintext credentials

## Procedure

1. Capture the defective response in full, with request, status, headers and body.
2. Construct the baseline: the same request under conditions where the product behaves correctly.
3. Change only the one variable that distinguishes baseline from defect, so the diff isolates the cause.
4. Capture the baseline identically and diff the two captures field by field.
5. State which difference is the defect and which differences are expected noise.
6. Attach both captures and the diff to the report so the claim can be audited without rerunning anything.

## Signals

- You are asserting a response is wrong without showing what right looked like in the same conditions.
- Baseline and defect captures differ in several fields, and you have not separated signal from noise.
- The baseline was captured under a different session or role, which invalidates the comparison.
- Reviewers ask what the correct response should be, and your answer is intuition rather than a capture.

## Patterns

**1. Diff line**

```text
field=status defect=200 baseline=403 field=body.count defect=37 rows baseline=0 noise=none
```

**2. Variable note**

```text
changed=user-id-in-path only effect=status-flips-to-200 implication=missing-ownership-check
```

**3. Pair record**

```text
defect-capture=2026-10-27T09:14Z baseline-capture=2026-10-27T09:16Z session=same role=same
```

## Pitfalls

- Building the baseline from a different role or session, which makes the diff prove nothing.
- Comparing responses captured minutes apart on a system that mutates between captures.
- Presenting the diff without labeling which difference constitutes the defect.
- Skipping the baseline because the wrongness feels obvious to you and only to you.

## Done when

- Both captures exist under identical conditions differing in exactly one variable.
- The diff is attached with the defect-bearing difference explicitly labeled.
- Expected noise fields are identified so a reviewer can dismiss them at a glance.

## References

- [OWASP - testing guidance for response comparison](https://owasp.org/www-project-web-security-testing-guide/)
- [CWE - weakness catalog](https://cwe.mitre.org/)
