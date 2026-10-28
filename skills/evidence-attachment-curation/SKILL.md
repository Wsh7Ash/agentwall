---
name: evidence-attachment-curation
description: "Curate the minimum evidence set that proves each claim, redacted and ordered to match the report, so reviewers get confirmation without a wall of screenshots to decode. Use when assembling attachments and you have more captures than claims or a pile of raw logs"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [evidence, reporting, redaction]
---

# Evidence Attachment Curation

> Curate the minimum evidence set that proves each claim, redacted and ordered to match the report, so reviewers get confirmation without a wall of screenshots to decode

**Use when:** assembling attachments and you have more captures than claims or a pile of raw logs

**Avoid when:** the platform limits you to a single pasted request-response pair that fits in the field

## Procedure

1. List each claim in the report and name the one artifact that proves it, dropping everything that proves nothing.
2. Order attachments to follow the report's section order so a reviewer can walk both in parallel.
3. Redact secrets, tokens and third-party personal data while keeping enough structure to remain verifiable.
4. Record what was redacted and why, so a missing field reads as deliberate rather than as a gap.
5. Check that each attachment is legible at normal zoom, since an unreadable capture is not evidence.
6. Verify no attachment contains a credential, internal hostname or path you would not publish.

## Signals

- Several attachments exist whose only purpose is showing that you did the work.
- Redaction removed the very field that would prove the claim, gutting your own evidence.
- Screenshots are cropped so tightly that the surrounding context identifying the asset is gone.
- A raw log contains a token or cookie that must not leave your machine with the report.

## Patterns

**1. Evidence map**

```text
claim=cross-tenant artifact=req-resp-pair-1.txt claim=scale artifact=count-note.txt claim=timing artifact=none-dropped
```

**2. Redact record**

```text
field=authorization header removed=yes reason=credential keep=structure-and-status note=declared-in-report
```

**3. Check line**

```text
legible=yes-zoom-100 no-credentials=yes no-internal-hostnames=yes order=matches-sections
```

## Pitfalls

- Attaching everything captured, which buries the two artifacts that actually prove the defect.
- Redacting after writing the narrative, so claims and evidence stop lining up.
- Shipping an unreadable screenshot whose contents you can vouch for but a reviewer cannot see.
- Forgetting a token in a raw capture, which turns a responsible report into a credential leak.

## Done when

- Each claim maps to exactly one proving artifact and attachments follow report order.
- Redactions are declared and no attachment contains a credential or internal-only detail.
- Every attachment is legible at normal zoom and identifies the asset it belongs to.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [CWE - weakness catalog](https://cwe.mitre.org/)
