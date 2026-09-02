# Budget Normalization — The Four-Lens Read

**Status:** method v0.1
**Purpose:** the concrete form of the differentiation. A nominal year-over-year delta is not an
analysis; it is a subtraction. This document specifies the four readings every budget line gets
before anything is said about it publicly.

---

## 1. The problem this fixes

A department page that reports "Corrections +8.4%" in green and "Education −0.9%" in red has
told the reader almost nothing, and has quietly told them one thing that is false: that up is
good and down is bad. Green there means only *went up*.

Four things are missing from that presentation, and all four are recoverable from public records:

1. Whether the increase is real or an artifact of the dollar
2. Whether the increase is real or an artifact of population
3. Whether the year is representative or a spike against trend
4. Whether the line is a proper object of that government at all

The fourth is the one a neutral instrument structurally cannot ask, and it is the reason this
instrument exists.

---

## 2. The four lenses

Applied in order. A finding does not leave the building until all four are recorded.

### L1 — Nominal delta
Straight year-over-year change from the adopted budget. Cite the document and page. This is the
number the competitor publishes; we publish it too, because omitting it looks evasive.

`Δnom = (FYn − FYn−1) / FYn−1`

### L2 — Real (inflation-adjusted)
Deflate both years to constant dollars before comparing.

`Δreal = ( (FYn / Pn) − (FYn−1 / Pn−1) ) / (FYn−1 / Pn−1)`

- **Deflator:** state the index used, its base year, and its source in the artifact. Use one
  index for the whole document; do not mix. CPI-U (BLS) is defensible and universally checkable;
  a state or sector-specific deflator is better where one exists and is public.
- **Never** apply an index whose vintage postdates the budget being analyzed without saying so.

### L3 — Per-capita
Divide by the served population, not the state population, wherever the served population is
published and different.

`PCn = FYn / POPn`, then compare `PCn` to `PCn−1`, and to `PCn` deflated (L2 × L3 combined).

- **Population source:** Census or the state's own published estimate, cited by vintage.
- For a school district, use enrollment (ADM), not district population. For corrections, the
  inmate population is the honest denominator *and* the state population is the honest one —
  they answer different questions. Report both or say which you chose and why.

### L4 — Proper object
The normative lens. Does this expenditure fall within the enumerated or granted authority of
**this** body, at **this** level?

Three categories, carried over from the fiscal-review method:

| Category | Meaning |
|---|---|
| **Clearly governmental** | Core function of this body under its own charter or enabling statute |
| **Gray zone** | Defensible under a broad reading; a reasonable citizen could object |
| **Constitutionally fraught** | Public funds to a particular private benefit — the "Not Yours to Give" tradition |

**These categories flag constitutional weight. They do not declare illegality.** Nothing in this
lens asserts that a fraught line is unlawful, and the artifact must say so in those words.

---

## 3. Trend before conclusion

A single-year delta is not a trend and must never be presented as one. Minimum **five fiscal
years** for any line the artifact characterizes as growing or shrinking. Where five years are
not available, say so and characterize nothing.

A department at +55.5% in one year may be: a genuine expansion, a one-time capital item, a
fund transfer, a reclassification, or a prior-year base that was itself depressed. **The delta
does not distinguish these and neither does the reader.** Establishing which it is, from the
budget document's own notes, is the work.

---

## 4. Worked template

Reported department deltas observed on the competitor's site — Corrections +8.4%, Health and
Human Services +4.6%, Education −0.9% (state aid −1.7%), Public Utilities Commission +55.5%,
Finance and Management +24.2% — are **illustrative targets, not inputs.** No figure enters an
artifact on the strength of a competitor's page. Re-derive every one from the adopted budget
before use.

Fill from primary sources only:

| Line | L1 nominal Δ | L2 real Δ | L3 per-capita Δ (real) | L4 category | 5-yr trend | Distinguishing note |
|---|---|---|---|---|---|---|
| _(department)_ | _(from adopted budget, p.__)_ | _(index: ___ , base ___)_ | _(pop source: ___ , vintage ___)_ | clearly governmental / gray / fraught | _(FY__–FY__)_ | _(capital? transfer? reclassification?)_ |

## 5. Mechanical checks before release

- Re-add every table and subtotal by hand; recompute every percentage from its base numbers
- Confirm the **actual funding source** of every criticized line — property tax vs. enterprise
  fund vs. special fund vs. federal pass-through — before characterizing who pays
- For any "modern tools could do this cheaper" claim, confirm the target is a **data task**, not
  physical work. Cost in dirt and labor is not addressable by software, and conflating the two
  is the fastest available way to lose a credible audience
- Where a descriptive label and an accounting code disagree, state a **documented question**,
  never an accusation

## 6. Output posture

The four-lens read produces a **question the government can answer from records it already
holds**, not a verdict. L4 supplies the normative weight; L1–L3 supply the arithmetic that
makes the question unavoidable. Neither half works alone: arithmetic without a normative floor
is the competitor's product, and a normative claim without arithmetic is an opinion column.
