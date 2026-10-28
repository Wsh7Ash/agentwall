# Changelog

All notable changes to `agentwall` are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions follow [SemVer](https://semver.org/).

## [1.0.0] - 2026-10-27

### Added

- Initial release: 50 unique bug-bounty operations skills across six phases
  (`program`, `queue`, `reproduce`, `report`, `followup`, `portfolio`).
- Validator with structural, strength and hygiene rules; `50/50 skills valid`
  gate with `--json` output for CI.
- Deterministic renderer and `build` command writing `skills/`,
  `pack.json` (SHA-256 per skill) and `results/`.
- CLI: `validate`, `list`, `show`, `search`, `build`, `queue`.
- `queue` — structured weekly queue report to phase-ordered ops runbook with
  thin-coverage warnings.
- Test suite (17 tests) covering corpus shape, rules, regeneration, drift and
  every CLI command.
- CI workflow, docs (`ARCHITECTURE`, `USAGE`, `PROJECT_SPEC`), `SECURITY.md`.

### Fixed

- `cmd_list`: the `--tag` and `--phase` filters were combined with wrong
  boolean precedence, so `--phase` alone returned all 50 skills. Both
  conditions are now parenthesised.