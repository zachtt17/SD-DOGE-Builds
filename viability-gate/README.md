# The Viability Gate

**Status: NOT PASSED. Set June 2026. Still open as of September 2026.**

Until this gate produces a number, no interactive matrix, no UI, and no build bake-off proceeds.
That is not caution — it is that every architecture decision downstream of this gate is
unfounded without it.

**Run it this week. On a legal pad. It does not require a computer.**

---

## 1. What the gate measures

**Human minutes per dot placement.**

A **dot placement** is one complete scored cell:

> one subject × one axis → one band on the scale, with (a) the citable public action, (b) the
> cited benchmark passage, and (c) a one-sentence reason a reader could disagree with.

Anything less than all three is not a placement and does not get timed as one. A band with no
citation is a guess, and timing guesses tells you how fast you can guess.

## 2. The protocol

**Subjects:** 10 South Dakota legislators.
**Axis:** exactly one — **A2, "Proper object of government"**
(see [`../docs/method/benchmark-conformance.md`](../docs/method/benchmark-conformance.md) §4).

A2 is the recommended axis because it is the hardest, it is the one the competitor's instrument
structurally cannot ask, and it is already exercised in the DOGE fiscal reviews. If the hardest
axis is fast, everything is fast. Timing an easy axis produces a number that flatters the
project and decides nothing.

### Steps

0. **Verify the roster first.** Pull the 10 names from an authoritative primary source — the
   Legislative Research Council or the Secretary of State — not from memory and not from a
   prior draft. Confirm no recent cycle changed the seat. Filter on "South Dakota": the
   Watertown, Wisconsin collision has produced roster errors before, and a roster error
   invalidates everything built on it.
1. **Commit the thresholds in §4 in writing, before scoring anything.** Sign and date the
   sheet. This is the whole anti-rationalization device; a threshold chosen after seeing the
   number is not a threshold.
2. **Pick the 10 without cherry-picking.** Suggested: 5 House, 5 Senate; a mix of urban and
   rural districts; at least 2 the operator is politically friendly toward and at least 2 he is
   not. Write down the selection rule *before* selecting.
3. **Score one placement at a time, with a stopwatch running per placement.** Stop the clock
   between placements. Do not time the batch and divide — the batch average hides the tail, and
   the tail is what kills a matrix.
4. **Record every placement on the tally sheet** ([`tally-sheet.md`](tally-sheet.md)), including
   the ones that come out as gaps.
5. **Mark gaps as gaps** (`—`, Insufficient public record). Gaps are fast and do not count as
   successful placements — record them in a separate column, because a fast run made of gaps is
   a failed run.
6. **Wait 48 hours. Blind re-score 2 of the 10** without looking at the first sheet.

## 3. The scaling arithmetic — the reason the number matters

South Dakota's legislature is **105 members** (70 House, 35 Senate). One axis across the full
chamber, and the full six-axis set:

| Median min/placement | 1 axis × 105 | 6 axes × 105 |
|---|---|---|
| 5 | 8.75 hr | 52.5 hr |
| 10 | 17.5 hr | 105 hr |
| 25 | 43.75 hr | 262.5 hr |
| 40 | 70 hr | 420 hr |

Then multiply by refresh cadence — a scorecard that is not re-run each session is a historical
document. **This table is the product decision.** At 40 minutes a placement, a six-axis
statewide matrix is ten work-weeks per session for one person, and it is not a product; it is a
second job. At 10 minutes it is two and a half weeks, and it is a product.

## 4. Pre-committed thresholds

Commit to these (or amend them in writing) **before** step 3. Judged on the **median** of the
10, not the mean — one pathological subject should not sink a viable instrument, and one easy
subject should not rescue a bad one.

| Result | Verdict | What happens next |
|---|---|---|
| **Median ≤ 10 min**, **≤ 2 gaps of 10**, blind re-score drift **≤ 1 band on both** | **PASS** | The interactive matrix is viable. The bake-off is now justified and gets run. |
| **Median 10–25 min**, gaps ≤ 3, drift ≤ 1 band | **CONDITIONAL** | Hand-scored artifacts only. Publish 3–5 per [`../docs/strategy/02-positioning.md`](../docs/strategy/02-positioning.md) §6. **No UI work.** Re-gate after the artifacts ship. |
| **Median > 25 min**, OR **≥ 4 gaps**, OR **drift > 1 band on either** re-score | **FAIL** | The matrix is not a product in this form. See §5. |

**The drift test is not a tiebreaker — it is a veto.** If a placement moves more than one band
on blind re-score, the problem is the *axis definition*, not the tooling, and no amount of
software fixes it. Speed with drift is worse than slow: it means fast, confident, irreproducible
numbers.

## 5. If it fails

Failure is a real outcome and it has a real next step. In order:

1. **Tighten the axis definition once** — most drift comes from an axis that silently asks two
   questions. Re-run the gate one time, on 10 *different* subjects.
2. **If it fails again: drop the statewide matrix.** Keep the local tier, where the operator has
   standing and the record is small enough to score honestly. Three DOGE fiscal reviews and
   local scorecards, done well and published, are worth more than a statewide matrix that
   cannot be maintained.
3. **Do not respond to a failed gate by adding build capacity.** The bake-off has sat staged
   since June while a funded competitor shipped. The bottleneck was never model capability or
   the choice among three candidate builds, and a fourth build agent will not move it.

## 6. What a passed gate does *not* authorize

- Not national build-out. The structural fence holds coverage to South Dakota — and, for
  federal questions, to South Dakota's own congressional delegation — until the SD vertical is
  proven with published artifacts that have survived a hostile reader.
- Not ingestion from a third-party site. That remains blocked on the terms-of-service item
  ([`../docs/strategy/01-competitive-assessment-pierre-review.md`](../docs/strategy/01-competitive-assessment-pierre-review.md) §7.3).
- Not merging the fiscal and scorecard instruments. That firewall is permanent.

## Files

| File | Purpose |
|---|---|
| [`tally-sheet.md`](tally-sheet.md) | Print this. One page. The actual instrument. |
| [`roster-template.csv`](roster-template.csv) | Blank by design — fill from a verified primary source |
| [`RESULT.md`](RESULT.md) | Empty until the gate runs. Record the number here. |
