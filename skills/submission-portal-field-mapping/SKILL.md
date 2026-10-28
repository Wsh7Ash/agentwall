---
name: submission-portal-field-mapping
description: "Map your prepared report into the platform's actual fields before you start typing, so mandatory fields get real content instead of a hurried paste that loses your structure. Use when submitting through a platform whose form fields do not match your report's sections"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reporting, submission, process]
---

# Submission Portal Field Mapping

> Map your prepared report into the platform's actual fields before you start typing, so mandatory fields get real content instead of a hurried paste that loses your structure

**Use when:** submitting through a platform whose form fields do not match your report's sections

**Avoid when:** you are emailing a single free-form report with no platform structure imposed

## Procedure

1. Open the submission form and list every mandatory field with the content type it expects.
2. Map each report section to a field, deciding what is shortened, what is moved and what does not fit.
3. Check field limits so a long reproduction section is not silently truncated at submission.
4. Prepare the mapped content in a local draft first, where a lost session cannot destroy the work.
5. Preserve the full report locally as the master copy regardless of what the form accepted.
6. After submission, re-read what the platform actually stored, since rendered output often differs from input.

## Signals

- A mandatory field has no natural home in your report and would otherwise receive a token sentence.
- The reproduction section is longer than the field limit with no plan for where the overflow goes.
- The platform's severity field uses a scale different from the one you drafted against.
- You have not checked what the platform rendered after a prior submission and assumed it matched.

## Patterns

**1. Field map**

```text
summary->title impact->description repro->steps-field overflow=link-to-attachment severity=critical-vs-high-note
```

**2. Limit check**

```text
field=repro max=4000 chars draft=5200 action=trim-or-attach full-text note=never-silent-truncate
```

**3. Render check**

```text
stored-differs=yes field=steps formatting=markdown-stripped action=adjust-source-formatting
```

## Pitfalls

- Pasting directly into the form so a session timeout discards the finished report.
- Letting the platform truncate your reproduction without noticing, which ships an incomplete finding.
- Mapping severity onto a differently-calibrated scale and inheriting a rating you did not argue.
- Skipping the post-submit re-read, so formatting damage or lost sections go to triage unseen.

## Done when

- Every mandatory field has mapped content and every field limit has been checked.
- The master copy of the full report exists locally, independent of the platform.
- The stored submission has been re-read and matches the intended content.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [CWE - weakness catalog for classification fields](https://cwe.mitre.org/)
