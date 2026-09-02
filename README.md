# SD DOGE Builds

Working repository for **The Correspondence** — a normative benchmark instrument for South
Dakota government, scored from school board to statehouse against the founding-era record.

This repo holds strategy, method, and the gate that decides whether any of it becomes software.
It does not yet hold software, and that is deliberate.

## The one-paragraph thesis

Descriptive legislative data is now a commodity in South Dakota. Bills, votes, statute diffs,
budget-by-category, interim transcripts, and rulemaking are all published by at least one
funded competitor. What nobody publishes is a **normative** instrument: a scored answer to
whether a given appropriation, ordinance, or vote is a proper object of the government that
took it, measured against a declared benchmark with a declared end-date. That instrument is
the product. Everything else is infrastructure to be consumed, not rebuilt.

## Current state (September 2026)

| Item | Status |
|---|---|
| Correspondence spec | v0.3, three-build bake-off staged and **not run** |
| Viability gate | **Not passed.** Blocks all interactive UI work — see [`viability-gate/`](viability-gate/) |
| Competitive picture | Reassessed Sept 2026 — see [`docs/strategy/01-competitive-assessment-pierre-review.md`](docs/strategy/01-competitive-assessment-pierre-review.md) |
| Scored artifacts published | 0 (three DOGE fiscal reviews exist; they are a *different* instrument — see below) |

## The two instruments, kept apart

This is a standing rule, not a preference. Mixing them destroys both.

- **Fiscal review** (Watertown DOGE method) — itemized, sourced, re-runnable questions about
  spending. **No individual official is scored.** Its credibility comes from the fact that a
  hostile reader cannot dismiss it as a weighting exercise.
- **Benchmark conformance** (The Correspondence) — individuals and measures *are* scored,
  against a declared and openly ideological benchmark set, with authorship disclosed.

A fiscal review that imports scores becomes a campaign document. A scorecard that hides its
authorship becomes an attackable one. See [`docs/method/`](docs/method/).

## Layout

```
docs/strategy/   what we decided and why, with the conditions that would reverse each decision
docs/method/     the instruments themselves — benchmark conformance, budget normalization
viability-gate/  the unpassed gate: protocol, tally sheet, decision rule
```

## Reading order

1. [`docs/strategy/01-competitive-assessment-pierre-review.md`](docs/strategy/01-competitive-assessment-pierre-review.md) — what exists, what is verified, what is not
2. [`docs/strategy/03-competitor-method-critique.md`](docs/strategy/03-competitor-method-critique.md) — their published scoring method, transcribed and questioned
3. [`docs/strategy/04-coverage-map.md`](docs/strategy/04-coverage-map.md) — which gaps are protected and which are merely empty
4. [`docs/strategy/02-positioning.md`](docs/strategy/02-positioning.md) — consume, don't compete; ship the instrument, not a portal
5. [`docs/strategy/00-decision-record.md`](docs/strategy/00-decision-record.md) — the standing decisions and their reversal conditions
6. [`viability-gate/README.md`](viability-gate/README.md) — the thing to do this week
