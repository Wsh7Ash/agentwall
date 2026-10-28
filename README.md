# agentwall

**50 validated bug-bounty operations skills, plus a CLI that turns a weekly queue report into a phase-grouped ops runbook.**

## The problem

Running bug bounty as a practice is mostly operations: choosing programs that fit, keeping the week's queue honest, reproducing findings so they survive triage, writing reports that get read, following up until decisions arrive, and reviewing the portfolio so next quarter's hours go somewhere better. The craft exists in scattered blog posts and threads, but almost never as checkable, ordered skill files — so every new week re-decides the operating procedure from scratch.

## What this repo does

`agentwall` is a corpus of **50 unique skills** organised into six phases of an operations arc — `program → queue → reproduce → report → followup → portfolio` — with a validator that enforces structural and quality floors on every skill, and a CLI whose domain command (`queue`) turns a structured weekly queue report into a phase-ordered runbook drawn from the corpus.

Every skill is a self-contained procedure with a summary, use/avoid guidance, a numbered procedure, observable signals, concrete patterns, pitfalls and completion criteria.

### Key features

- **50 skills, all validated**: `validate` enforces 6+ steps, 4+ signals, 3+ patterns, 3+ pitfalls, 180+ words, canonical `https` references, no placeholder tokens, no machine-local paths, unique slugs and titles, and byte-identical agreement with the files on disk.
- **`queue`**: turns a JSON week file (program, state, tags per item) into a phase-ordered runbook, scoring the corpus against the week's vocabulary and flagging phases with thin coverage.
- **`validate`**: the "50/50 valid" gate. Exits non-zero on any violation, with `--json` for CI.
- **`build`**: deterministically regenerates `skills/`, `pack.json` (SHA-256 per skill) and `results/`.
- **`list` / `show` / `search`**: browse and search the corpus locally, no network required. `list --phase` filters to one phase.
- **Zero runtime dependencies**: Python standard library only; `pytest` is the single dev dependency.

### Terminal example

```console
$ python -m agentwall validate
agentwall: 50/50 skills valid
  ok  steps>=6 signals>=4 patterns>=3 pitfalls>=3 words>=180 refs canonical https

$ python -m agentwall queue --week-file examples/demo-week.json
# Weekly ops runbook - 2026-W44
Queue items: 4   Programs: 2   Skills matched: 26 of 50   Plan steps: 12

Thin coverage (no matched skill in these phases): report, followup, portfolio

## program

duplicate-policy-review  (match 2)
  Understand how a program treats duplicates, race conditions and partial findings before you hunt, ...
  ...

$ python -m agentwall search reproduction evidence
  5  cross-account-reproduction                   Cross Account Reproduction
  5  environment-matrix-reproduction              Environment Matrix Reproduction
  ...
```

## Skill phases

| Phase | Count | Covers |
|---|---|---|
| `program` | 8 | fit scoring, scope interpretation, safe harbor, reward analysis, health checks, channel setup, duplicate policy, capacity allocation |
| `queue` | 9 | weekly queue construction, backlog triage, effort banding, timeboxing, context switching, WIP limits, pruning, promotion gates, tooling readiness |
| `reproduce` | 8 | clean-room repro, environment matrix, reduction, prerequisite chains, cross-account, baselines, flake rates, consistency reruns |
| `report` | 9 | structure, impact framing, step clarity, severity rationale, evidence curation, PoC narration, remediation guidance, editing, portal mapping |
| `followup` | 8 | triage replies, clarification loops, duplicate negotiation, bounty verification, retests, disclosure timing, relationship maintenance, escalation |
| `portfolio` | 8 | monthly metrics, acceptance review, earnings trends, skill gaps, technique investment, positioning, annual goals, program exit |

## Install

```shell
python -m pip install -e ".[dev]"
```

## Usage

```shell
export PYTHONPATH=src                          # or install with pip -e
python -m agentwall validate                   # the 50/50 gate
python -m agentwall validate --json             # machine-readable, for CI
python -m agentwall build                       # regenerate skills/, pack.json, results/
python -m agentwall list --phase queue           # one phase
python -m agentwall show weekly-queue-construction
python -m agentwall search duplicate payout
python -m agentwall queue --week-file examples/demo-week.json
python -m pytest -q                             # 17 passed
```

## Install as agent skills

Each `skills/<slug>/SKILL.md` is a self-contained skill file with YAML front-matter, loadable by Claude Code, opencode, or any runtime that reads `SKILL.md` corpora. Copy the `skills/` directory into your agent's skills path, or consume `pack.json` as the index.

## Scope and ethics

This pack plans, documents and reviews **authorized** testing. It contains no exploitation technique, no payload, and no instruction to test anything outside a program's declared scope. Run everything you build here inside an authorized scope.

## Documentation

- [`docs/PROJECT_SPEC.md`](docs/PROJECT_SPEC.md) — what the pack is and is not
- [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) — corpus, validator, renderer, CLI
- [`docs/USAGE.md`](docs/USAGE.md) — command-by-command walkthrough
- [`RESULTS.md`](RESULTS.md) — executed validation evidence

## License

MIT