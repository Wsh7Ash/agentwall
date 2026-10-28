# Results

Reproducible evidence for the claims in `README.md`.

## Environment

- OS: Windows (MSYS2 shell), Python 3.14
- Runtime: Python 3.10+ standard library, `pytest` as dev dependency
- Dependency manager: `pip` in a clean venv (`python -m venv`)
- Network: none required at any point

## Validation performed

| Gate | Result |
|---|---|
| install (`pip install -e ".[dev]"` in a clean venv) | PASS |
| console script (`agentwall validate` from the venv) | PASS |
| build (`agentwall build`) | PASS (exit 0) |
| validation gate (`agentwall validate`) | PASS — **50/50 skills valid** |
| unit tests (`pytest -q`) | PASS — **17 passed** |
| demo run (`queue`, `search`, `list --phase`) | PASS |
| secret scan | PASS (0 hits) |

## Commands executed

```shell
export PYTHONPATH=src
python -m agentwall build                     # regenerates skills/, pack.json, results/
python -m agentwall validate                  # exit 0, prints 50/50
python -m pytest -q                           # 17 passed
python -m agentwall queue --week-file examples/demo-week.json --top 24 > results/queue-demo.md
python -m agentwall search "reproduction evidence" --limit 5 > results/search-example.txt
grep -rInE "(ghp_|github_pat_|AKIA[0-9A-Z]{16}|-----BEGIN [A-Z ]*PRIVATE KEY)" \
  --exclude-dir=.git --exclude=RESULTS.md .   # RESULTS.md quotes the pattern itself
```

Clean-venv install (the gate the system interpreter refuses under PEP 668):

```shell
python -m venv /tmp/bo-venv
/tmp/bo-venv/bin/python -m pip install -e ".[dev]"
/tmp/bo-venv/bin/agentwall validate     # 50/50 skills valid
/tmp/bo-venv/bin/python -m pytest -q    # 17 passed
```

## Observed result

```
agentwall: 50/50 skills valid
  ok  steps>=6 signals>=4 patterns>=3 pitfalls>=3 words>=180 refs canonical https
```

```
# Weekly ops runbook - 2026-W44
Queue items: 4   Programs: 2   Skills matched: 26 of 50   Plan steps: 24

Thin coverage (no matched skill in these phases): portfolio
```

Phase distribution across the corpus:

```
program 8, queue 9, reproduce 8, report 9, followup 8, portfolio 8  = 50
```

`pytest -q` reports `17 passed` with no warnings. Secret scan returns no matches
(the only line it can match is this file quoting its own pattern, hence the
`--exclude=RESULTS.md`).

## Generated artifacts

- `results/catalog.md` — the 50-skill index table
- `results/validation.json` — machine-readable gate report
- `results/queue-demo.md` — runbook produced from `examples/demo-week.json`
- `results/search-example.txt` — keyword ranking output
- `pack.json` — manifest with a SHA-256 per skill file

## Known limitations

- The system Python is externally managed (PEP 668), so `pip install -e .` fails there by design; the venv run above is the install evidence.
- `queue` ranks by vocabulary substring overlap. It is a planning aid, not a scheduling engine: it never decides hours, only which skills the week's vocabulary points at.
- Thin-coverage output for a 4-item demo week legitimately omits phases the week does not touch; a fuller week would cover more phases.
- The word floor is a floor, not a quality guarantee: content judgment remains a reviewer's job.