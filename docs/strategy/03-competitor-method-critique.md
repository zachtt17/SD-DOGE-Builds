# Competitor Method Critique — Pierre Review "Issue Stance Scores"

**Prepared:** September 2026
**Source:** *How Issue Stance Scores Work*, Pierre Review blog, dated **February 28, 2026**,
served at **sdlegtracker.com** — captured from operator screenshots 2026-09-02.
**Evidence tier:** **Verified** — this is the vendor's own published methodology in its own
words. Direct re-load is blocked by this session's egress proxy for both `pierrereview.com`
and `sdlegtracker.com`; the transcription below is from the captured page.

> **Domain note.** Pierre Review is served on at least two domains: `pierrereview.com` and
> `sdlegtracker.com`. Assume they are the same product until shown otherwise, and record
> whichever domain a citation came from.

---

## 1. What they actually built

This is materially more sophisticated than the "88% party loyalty" figure on the district
pages, and the earlier read in [`01-competitive-assessment-pierre-review.md`](01-competitive-assessment-pierre-review.md)
understated it. The party-loyalty number is a headline metric sitting on top of a real
per-issue scoring engine.

### Transcribed method

- **Output:** per-legislator, per-issue score from **−100** (consistent opposition) to **+100**
  (consistent support)
- **Issues are directional action phrases** — e.g. "reduce property tax rates,"
  "strengthen election security," "incentivize economic development," "expand renewable energy
  incentives," "expand school choice," "expand Medicaid coverage," "increase criminal
  penalties," "strengthen child welfare protections"
- **Taxonomy:** **138 canonical policy issues** under **20 topic categories**
- **Per bill:** 1–5 relevant issues identified from the canonical list; each gets two values —
  - **Stance** (−1.0 to +1.0): what a *Yea* vote on this bill means for this issue
  - **Relevance** (0.0 to 1.0): how central this issue is to the bill
- **Procedural bills** (appointments, commemorations, scheduling) receive no stances
- **Aggregation:**
  ```
  contribution   = vote_direction * bill_stance * relevance * recency_weight
  raw_score      = sum(contributions) / sum(weights), clamped to [-1, +1]
  display_score  = round(raw_score * 100), range: -100 to +100
  confidence     = min(1.0, scored_votes / 15)
  ```
  with `vote_direction` = +1 Yea, −1 Nay; current-session votes weighted above prior-session
- **Pipeline:** Bill Text (**title + summary**) → Issue ID (1–5 per bill) → Vote Records
  (yea/nay) → Aggregation → Stance Profile
- **Their stated limit:** *"These scores describe voting behavior — how a legislator has voted
  on bills touching each issue. They do not represent personal beliefs, campaign positions, or
  intent."*

**Credit where due:** publishing the formula, disclaiming intent, and shipping a confidence
measure are all more discipline than most scorecards manage. This critique is not a claim that
they are careless.

---

## 2. The strategic consequence — read this before the criticisms

**They have built the substrate a normative scorecard needs, and stopped one step short of it.**

A per-bill table of (issue, stance, relevance) plus vote records is precisely the input a
benchmark scorecard consumes. The only thing separating their output from a Liberty-Index-style
score is a **weight vector over the 138 issues** expressing what *ought* to be — plus a
justification for each weight.

That is not a six-month engineering problem. It is a weekend of arithmetic on top of their
table. Which means:

1. **The moat is thinner than the earlier assessment claimed.** It is not "they can't build
   it." It is one dot product away.
2. **The moat is also better defined.** What cannot be cheaply copied is not the arithmetic —
   it is the *declared, cited, end-dated justification for each weight*, and the willingness to
   sign one's name to it. That is the entire product, and it is exactly what
   [`../method/benchmark-conformance.md`](../method/benchmark-conformance.md) specifies.
3. **The trip-wire from §5 of the competitive assessment is now more urgent.** Their
   `/integrations` page is where a third party's weight vector would appear. Watch it.

**Corollary:** the correct posture toward this taxonomy is neither imitation nor avoidance.
It is to build our weight vector against *our own* axis definitions
([`../method/benchmark-conformance.md`](../method/benchmark-conformance.md) §4), keep it
publishable independent of their data, and treat any future access to their per-bill table as
an accelerator we do not depend on.

---

## 3. Documented questions about the method

Framed per the DOGE Axis-2 rule: where the record is ambiguous, state a **question the
publisher can answer**, never an accusation. Each of these is answerable by Pierre Review from
material they already hold.

### Q1 — The topic chart does not sum to the stated total
The published chart shows the **top 12 of 20** topics by mapped issues:

| Topic | Issues |
|---|---|
| Healthcare & Medicaid | 23 |
| Business & Economy | 21 |
| Public Safety | 19 |
| Elections & Government | 14 |
| Tax Policy | 13 |
| State Budget | 12 |
| Agriculture & Wildlife | 12 |
| Energy & Environment | 10 |
| K-12 Education | 9 |
| Social Services | 9 |
| Housing & Local Gov | 7 |
| Labor & Employment | 7 |
| **Sum of top 12** | **156** |

The caption reads "Total: 138 issues," and eight further topics are not shown. **156 > 138
before the remaining eight topics are counted.**

The likely benign explanation is that the mapping is many-to-many — one canonical issue mapped
under several topics — which the word "mapped" supports. If so, the chart is counting mappings
while the caption is counting issues, and the two are not the same quantity.

*Question:* is an issue mappable to more than one topic, and does the caption count distinct
issues while the bars count mappings?

**Why this matters to us, not just to them:** this is the exact failure the fiscal-review
method's mechanical check exists to catch — *a published table whose figures do not reconcile
discredits the instrument regardless of the analysis behind it.* Re-add every table before
release. No exceptions, including for our own.

### Q2 — Issue identification runs on title + summary
The published pipeline diagram names the input as **"Bill Text — title + summary,"** not
enrolled text and not amendments.

In South Dakota this is a live problem, not a theoretical one: a **hoghouse amendment** can
replace a bill's entire content while the title survives. Any tagging derived from title and
summary can carry the pre-amendment issue set into a post-amendment vote.

*Question:* are issues re-identified after amendment, and against which version of the text?

### Q3 — Yea/Nay only, on bills
`vote_direction` is defined as +1 Yea, −1 Nay, and procedural *bills* are excluded. Nothing
published addresses **procedural motions on substantive bills** — motions to table, to defer to
the 41st day, or to refer — which in this legislature are frequently where a bill actually
dies.

A legislator can score +80 on "reduce property tax rates" from final-passage votes while having
voted to defer the only bill that would have done it.

*Question:* do motion votes on substantive bills contribute to stance scores, and are excused
or absent members distinguished from Nay?

### Q4 — Full-magnitude scores on thin records
*(Amended: their April 2026 election post states a real no-record rule — a candidate with no
voting record is left blank rather than scored. Credit that. The question below concerns the
thin-record incumbent, which that rule does not reach. See
[`04-coverage-map.md`](04-coverage-map.md) §1.)*

`confidence = min(1.0, scored_votes / 15)` is computed and displayed, but the score itself is
not attenuated by it. A legislator with one relevant vote can display **−100 at confidence
0.07**, rendered on the same diverging bar as a fifteen-vote score.

This is the thin-record problem in a different costume: a number that looks complete standing
in for a record that is not. Our instrument's answer is the `—` gap marker, reported separately
and never averaged ([`../method/benchmark-conformance.md`](../method/benchmark-conformance.md) §3).

*Question:* is the displayed score attenuated, suppressed, or flagged below a confidence floor?

### Q5 — Stance and relevance values are unattributed
The worked example assigns `stance=+0.85, relevance=0.90` with no published account of who or
what assigns them, whether a human reviews them, or what the error rate is. These values are
almost certainly model-assigned, which is a reasonable engineering choice and an unaudited one.

*Question:* how are stance and relevance assigned, and has any sample been human-audited?

### Q6 — The formula is published; the inputs are not
Publishing `contribution = vote_direction * bill_stance * relevance * recency_weight` is
genuine transparency about *shape*. But without the per-bill `(issue, stance, relevance)` table
and the recency-weight function, **no outside party can re-derive a single score.**

This is the difference between *transparent* and *re-runnable*, and it is a differentiator we
should take deliberately: our per-item table publishes with the artifact. Itemized, sourced,
and re-runnable beats a score nobody can audit — including a score whose formula is public.

*Question:* is the per-bill stance/relevance table available, and under what terms?

---

## 4. The finding that matters most: an undeclared normative frame

Their disclaimer is that the scores describe behavior, not belief. Granted. But the **taxonomy
is not neutral, and its non-neutrality is not disclosed.**

Issues are *directional action phrases*, and someone chose every direction:

- "**expand** Medicaid coverage" — not "restrain Medicaid growth"
- "**expand** school choice" — not "protect district school funding"
- "**incentivize** economic development" — not "limit targeted business subsidies"
- "**increase** criminal penalties" — not "restrain the criminal code"
- "**strengthen** election security" — not "reduce barriers to voting"

Each pair names the same axis from opposite ends. Choosing which end is the *named action*
sets the sign convention for every score on that axis, and it is a choice with a worldview
behind it — visibly a mix of frames rather than one, which is what you would expect from a
taxonomy assembled for coverage rather than derived from a stated commitment.

**The worked example makes the embedded theory explicit.** On a property-tax-relief bill they
assign `reduce government spending: stance = −0.60`, with the stated reason that the bill
reduces revenue. That encodes a contestable fiscal proposition — that cutting revenue counts
*against* spending restraint — and it is not merely scored neutral (0.0) but actively negative.
The practical result: **a legislator who votes for tax relief has their "reduce government
spending" score pushed down.** A reader from this audience would call that backwards, and the
argument about whether it is backwards is a normative argument, conducted inside a tool that
says it is not making one.

**This is the single strongest point in our favor, and it is not "they are biased."** It is:

> There is no neutral taxonomy. Every scoring instrument encodes a frame. The only honest
> choices are to declare yours or to leave it undeclared. We declare ours on page one, cite it
> to a dated record, and publish the table so you can re-derive every number and disagree with
> the weighting rather than the facts.

Make that argument about the *structure of measurement*, never about their motives. It is
stronger, it is true, and it survives them reading it.

---

## 5. What this changes in our own build

| Their choice | Our answer |
|---|---|
| Directional phrases with undeclared frame | Axes derived from declared benchmark frames with cited end-dates |
| Score magnitude independent of record depth | `—` gap marker, reported separately, never averaged |
| Tagging from title + summary | Score the action actually taken; re-check after amendment |
| Formula public, inputs withheld | Per-item table publishes with the artifact |
| Yea/Nay on bills | Score the vote that decided the outcome, including motions |
| Unattributed stance values | Every placement carries a citation and a one-line reason a reader could dispute |

None of these require software. All of them require discipline, and the discipline is the
product.

---

## 6. Verification items added

| # | Item | Status |
|---|---|---|
| 3.1 | Re-load the methodology page from an unblocked network; confirm transcription verbatim | Open |
| 3.2 | Confirm relationship between `pierrereview.com` and `sdlegtracker.com` | Open |
| 3.3 | Determine whether the remaining 8 topic categories are published anywhere | Open |
| 3.4 | Check whether displayed scores carry a visible confidence floor | Open |
| 3.5 | Check `/integrations` for any third-party normative scorecard | Open — trip-wire |
