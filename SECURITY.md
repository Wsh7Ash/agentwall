# Security Policy

## Authorized use only

`agentwall` is a knowledge corpus and planning tool for **authorized** bug-bounty work: choosing programs, planning weeks, documenting and reviewing findings from testing that a program's rules explicitly permit. The software itself performs no network requests — it renders, validates and plans locally.

The skills describe operations methodology. They contain no weaponized exploit material: the corpus is deliberately about what surrounds the testing itself — program selection, queue discipline, reproduction quality, report writing, follow-up and portfolio review.

## Scope discipline is built into the corpus

The opening skills exist to keep hunting work authorized and bounded:

1. `scope-clause-interpretation` — every ambiguous scope clause resolves to a narrow reading before testing begins.
2. `safe-harbor-position-review` — what protection a program actually grants is established in writing first.
3. `reporting-channel-setup` — the authorized reporting path is confirmed before it is needed.
4. `weekly-queue-construction` — queued work is ranked against capacity, so nothing drifts into unauthorized territory by default.

The `queue` runbook orders these ahead of any testing work in later phases.

## What this repository contains

- Methodology, checklists and diagnostic patterns for operating an authorized bug-bounty practice.
- No exploit payloads, no credential harvesting techniques, no phishing material, no evasion guidance.
- No live target data, no credentials, no personal data. The example week file (`examples/demo-week.json`) is synthetic.

## Reporting a vulnerability in this project

If you find a defect in `agentwall` itself (for example, a validation bypass that lets a malformed skill pass the gate), please open a private security advisory on the repository or contact the maintainer through GitHub. Do not publish exploit details before a fix is available.

## Scope of this project's own testing

All tests run locally against the checked-in corpus and synthetic example files. No test sends traffic anywhere; the `queue` command operates on a checked-in JSON week file. Continuous integration runs the same local gates: validation, unit tests and an artifact-sync check.