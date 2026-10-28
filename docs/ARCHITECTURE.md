# Architecture

## Goals

1. **One source of truth.** Skills are authored as Python data; Markdown files are generated. A test asserts committed files match a fresh render, so the two can never disagree.
2. **Validation is a first-class gate.** Every quality floor lives in `validate.py` and is enforced by both the CLI and the test suite.
3. **No runtime dependencies.** Standard library only, so the pack runs anywhere Python 3.10+ exists.

## Components

```text
src/agentwall/
├─ corpus/           authored skill data (source of truth)
│  ├─ __init__.py    PACK metadata + loads part1..part3
│  ├─ part1.py       skills 1-17   (program, queue)
│  ├─ part2.py       skills 18-34  (reproduce, report)
│  └─ part3.py       skills 35-50  (followup, portfolio)
├─ model.py          Skill dataclass + strict dict loading
├─ render.py         deterministic SKILL.md + pack.json + results writer
├─ validate.py       every rule, one place
└─ cli.py            validate / list / show / search / build / queue
```

### Data flow

```text
part1..part3 (dicts)
      │  skill_from_dict()  -- shape check, rejects missing/empty fields
      ▼
   Skill (frozen dataclass)
      │
      ├─ validate_pack()  ─▶ Issue list ─▶ CLI exit code (0 only at 50/50)
      └─ render_skill()   ─▶ skills/<slug>/SKILL.md  (byte-deterministic)

queue (week.json)
      │  score corpus against the week's vocabulary (programs, tags, states)
      ▼
   phase-ordered runbook  (program → queue → reproduce → report → followup → portfolio)
      with thin-coverage warnings for phases that matched nothing
```

### The queue command

`queue` is agentwall's domain command and separates this pack from a document library. It consumes a small week file:

```json
{
  "week": "2026-W44",
  "items": [
    {"program": "alpha", "state": "retesting", "tags": ["idor", "orders"]}
  ]
}
```

Vocabulary is aggregated across every item (program names, tags, and state strings with hyphens normalised to spaces), then every skill is scored against that vocabulary by substring hits in slug, title, summary and tags. Matches are ordered by `PHASE_ORDER` and capped at `--top`, and phases with no matched skill are reported as thin coverage so an unaddressed part of the week is visible rather than silent.

### Design decisions

- **`queue` is intentionally small.** It encodes vocabulary matching and phase ordering, not a scheduling policy engine. How many hours to spend and in what order is judgment the reader keeps, and the thin-coverage warning makes gaps explicit instead of guessing.
- **Vocabulary aggregation, not per-item matching.** The plan reflects the whole week's workload. A runbook scoped to one queue item would systematically under-serve the other three.
- **Phase order lives in one constant.** `PHASE_ORDER` in `cli.py` drives both the runbook output and the thin-coverage calculation, so they can never disagree.

### Validation layers

| Layer | Where | Enforces |
|---|---|---|
| Shape | `model.skill_from_dict` | required keys, non-empty entries, `(label, code)` pattern pairs |
| Skill rules | `validate.skill_issues` | slug/title format, summary/use/avoid length, description window, tag format, step/signal/pattern/pitfall/done floors, reference format, word floor, placeholder and local-path hygiene |
| Pack rules | `validate.pack_issues` | exact skill count (50), unique slugs and titles |
| Disk sync | `cli.cmd_validate` | committed `SKILL.md` matches a fresh render byte for byte |

The CLI exits `0` only when every layer passes, which is what "50/50 valid" means.
