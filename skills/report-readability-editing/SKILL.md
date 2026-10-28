---
name: report-readability-editing
description: "Edit the finished report for a reader who is skimming under time pressure, cutting redundancy, front-loading facts and turning dense paragraphs into scannable structure. Use when the draft is accurate but long, dense, or written in the order you discovered things rather than the order they matter"
pack: agentwall
version: 1.0.0
category: defensive-security
tags: [reporting, writing, quality]
---

# Report Readability Editing

> Edit the finished report for a reader who is skimming under time pressure, cutting redundancy, front-loading facts and turning dense paragraphs into scannable structure

**Use when:** the draft is accurate but long, dense, or written in the order you discovered things rather than the order they matter

**Avoid when:** the report is already a tight few hundred words with facts leading

## Procedure

1. Read only the first sentence of every paragraph and check the report's spine still tells the whole story.
2. Move any fact that a reviewer needs early, such as asset or impact, up out of the paragraph it got buried in.
3. Cut sentences that repeat a claim already proven, keeping the strongest single statement of each point.
4. Convert lists of more than four items into structure with headings so scanning has anchors.
5. Replace jargon that the program's team would not use with plain descriptions of observed behavior.
6. Do a final pass for reading rhythm: short sentences after long ones, no paragraph that requires two passes.

## Signals

- The same impact claim appears three times in different words, which reads as padding rather than emphasis.
- The asset under test is not visible in the first paragraph.
- Paragraphs run long enough that a skimming reviewer loses the thread halfway through.
- You used internal shorthand that the program's engineers would have to decode.

## Patterns

**1. Spine read**

```text
1st-sentence-1=what-is-wrong 1st-sentence-2=where 1st-sentence-3=impact verdict=spine-holds-or-reorder
```

**2. Cut record**

```text
removed=duplicate-impact-line count=2 kept=strongest reason=repetition-reads-as-padding
```

**3. Front-load note**

```text
moved=asset-name line=7->1 reason=reviewer-needs-target-immediately
```

## Pitfalls

- Editing for length until a necessary precondition disappears along with the padding.
- Reordering facts into a logical structure that no longer matches how the defect was found, breaking repro.
- Removing repetition that was actually clarification, leaving a claim under-explained.
- Cutting evidence references while trimming prose, so claims outlive their support.

## Done when

- The first paragraph alone states what is wrong, where, and what an attacker gains.
- No claim is repeated without adding new information.
- Every paragraph survives a single-pass read without rereading.

## References

- [ISO 29147 - vulnerability disclosure](https://www.iso.org/standard/72311.html)
- [OWASP - testing guidance for reporting quality](https://owasp.org/www-project-web-security-testing-guide/)
