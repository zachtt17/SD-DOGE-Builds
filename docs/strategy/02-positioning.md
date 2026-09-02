# Positioning — Ship the Instrument, Not the Portal

**Prepared:** September 2026
**Supersedes:** the portal-shaped reading of Correspondence spec v0.3 (does not supersede the
spec's corpus, benchmark, or fence decisions, which stand)

---

## 1. The decision

**Do not build a portal.** Do not build ingestion, a search index, a bill tracker, a vote
database, or an interactive matrix UI at this time.

**Build the instrument:** a published methodology plus a small number of scored artifacts that
are unimpeachable on sourcing. Three to five artifacts, not fifty. Each one traceable to
primary records by any hostile reader with a library card.

## 2. Why the strategic move is *consume*, not *compete*

Pierre Review's engineering — ingestion, statute diffs, vote records, budget tables — is the
half of the original spec that costs the most and differentiates the least. Rebuilding it
spends six months to arrive at parity with a shipped product, and arrives with zero of the
thesis built.

The thesis is normative scoring against a declared benchmark. That work is bounded by *reading
and judgment*, not by pipelines. It does not require their data, an API, or any ingestion layer
to begin. It requires the primary record, which is already public.

> **The tension worth naming.** "Consume them as infrastructure" and "ship the instrument, not
> a portal" pull in different directions if taken literally. Consuming a monetized site means
> either a licensed API or scraping — and until [§7.3 of the competitive assessment](01-competitive-assessment-pierre-review.md#7-open-verification-items)
> is answered, neither is a decision that can responsibly be made.
>
> The resolution: **the near-term instrument needs no ingestion at all.** A hand-scored,
> hand-sourced artifact set is built from the LRC record, the adopted budget, and the meeting
> minutes — sources that are free, primary, and unencumbered. Consumption becomes a live
> question only at the scale where hand-scoring stops working, and the viability gate is what
> tells us where that line is. Until then, "consume, don't compete" means **do not rebuild
> what they built** — not "take a dependency on them."

**Consequence worth stating plainly:** the immediate deliverable requires no engineering.
That is why the stalled bake-off was never the bottleneck.

## 3. Where the differentiation actually lives

| Their instrument | Ours |
|---|---|
| Descriptive: what happened | Normative: whether it was a proper object of that government |
| Directional issue stances with an undeclared frame | Conformance to a declared benchmark with a declared end-date |
| Nominal year-over-year delta, green = up | Nominal, real, per-capita, and proper-object — four lenses |
| Undeclared authorship, sold as neutrality | Declared authorship, published rubric, re-runnable by a critic |
| Formula published, per-bill inputs withheld | Per-item table published with the artifact |
| State level only | School board → city council → county → statehouse → delegation |

The local tier is the defensible ground. It is unoccupied, the operator has standing there
rather than an opinion, and the artifacts already exist in draft.

## 4. The two fences (unchanged from spec v0.3)

- **No analysis fence at any level of government.** School board, city council, county
  commission, legislature, and the federal delegation are all in scope for *analysis*. Nothing
  is off limits to scrutiny on grounds of level.
- **Structural fence on build-out.** National coverage is held to South Dakota's own
  congressional delegation until the SD vertical is proven. No other state, no other
  delegation, until the gate passes and the artifact set is published and has survived contact
  with a hostile reader.

The fences are not the same kind of rule. The first is a principle. The second is a schedule,
and it expires on evidence.

## 5. The attack to expect, and the only answer to it

> *"You're laundering your politics through dead men."*

There is no clever rebuttal. There is only method:

1. **Owned authorship.** The rubric is disclosed as classical-liberal and Protestant in
   derivation, on the first page, every time. Never presented as neutral civic education with
   the lineage hidden. A skeptical reader who traces a concealed lineage finds the concealment
   more damaging than disclosed partisanship would have been.
2. **Declared end-dates.** Each benchmark frame states where its record closes and why. A frame
   without a stated terminus is an invitation to cherry-pick across two centuries.
3. **Thin-record honesty.** No public record on a criterion means "Insufficient public record,"
   scored as a gap — never a manufactured score with a hedging footnote. Fabricated-but-hedged
   scores are the most attackable element any scorecard can contain.
4. **Re-runnability.** Rubric, weights, sources, and scale published so a critic can re-derive
   every score and disagree with the *weighting* rather than the *facts*. Itemized, sourced,
   and re-runnable beats a score nobody can audit.

Method is described in [`../method/benchmark-conformance.md`](../method/benchmark-conformance.md).

## 6. What "shipped" means for this phase

The phase is complete when all of the following are true:

- [ ] Viability gate run and its number recorded ([`../../viability-gate/`](../../viability-gate/))
- [ ] Benchmark frames published with end-dates and rationale
- [ ] Scoring scale and weights published, weights summing correctly, arithmetic hand-checked
- [ ] 3–5 scored artifacts published, each fully sourced to primary records
- [ ] At least one artifact scores a subject the operator is politically friendly toward, and
      the score is not flattering. Absent this, the instrument is a campaign tool with extra steps.
- [ ] One "What This Scorecard Could Not Determine" section per artifact, written thick

The last two are not optional garnish. They are the credibility engine, and they are the two
most likely to be dropped under deadline.
