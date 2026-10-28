# Project Spec — agentwall

## Name

`agentwall`

## Category

`defensive-security`

## Target user

Individual bug-bounty hunters and small research teams who run hunting as an ongoing practice and need a repeatable operating procedure rather than another list of techniques.

## Problem

Bug bounty work is mostly operations: choosing programs that fit, keeping a weekly queue honest, reproducing findings so they survive triage, writing reports that get read, following up until a decision arrives, and reviewing the portfolio so next quarter's hours go somewhere better. This methodology lives in scattered blog posts and threads. Each new week re-decides the same things: what enters the queue, how effort is banded, when a reproduction is trustworthy, what evidence proves impact, how long to chase a stalled report, and which skill gap actually cost the most findings. Nothing is machine-checkable, and agents have no structured skill files to load.

## Solution

A corpus of 50 unique, validated operations skills organised into the six phases of an operations arc, with a validator that enforces quality floors and a CLI that turns a structured weekly queue report into a phase-ordered runbook with thin-coverage warnings.

## Core workflow

```text
author/edit corpus  ->  build  ->  skills/ + pack.json + results/
                                    |
                                    v
                          validate (50/50 gate)  ->  pytest  ->  CI
                                    |
                                    v
                       queue --week-file week.json -> ordered runbook
```

## Must-have features

- 50 unique skills with unique slugs and titles, covering program, queue, reproduce, report, followup, portfolio.
- Validator with structural, strength and hygiene rules; exit `0` only at 50/50.
- Deterministic renderer; committed files proven in sync by tests.
- `queue` producing a phase-ordered runbook from a JSON week file, with phase coverage gaps surfaced.

## Nice-to-have (explicitly out of scope for v1)

- Calendar integration or automatic hour scheduling.
- Direct platform API integration for report status.
- A scoring model beyond vocabulary matching.

## Acceptance tests

1. `validate` exits 0 and reports 50/50.
2. `pytest -q` passes 17 tests, including regeneration equality, drift detection and the queue round-trip.
3. `queue` — round-trips the checked-in example week file.
4. A generated build lands byte-identically in a clean temp directory.