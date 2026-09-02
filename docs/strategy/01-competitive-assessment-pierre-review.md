# Competitive Assessment — Pierre Review

**Prepared:** September 2026
**Subject:** pierrereview.com — South Dakota legislative intelligence platform
**Verdict:** Not a competitor to The Correspondence. Infrastructure to consume, and a live
threat to only one lane (see §5).

> **Amended 2026-09-02.** Their published scoring methodology surfaced after this document was
> first drafted and shows a full per-issue stance engine — 138 canonical issues, per-bill
> stance and relevance weighting, recency, and a confidence measure — not the thin
> party-loyalty metric §5 originally described. The strategic conclusion below survives; the
> characterization of their sophistication did not. See
> [`03-competitor-method-critique.md`](03-competitor-method-critique.md), which supersedes §5's
> reading of their scoring.

---

## 1. Evidence discipline for this document

This assessment scores a competitor, not a public official, but the same rule from the
DOGE method applies: **an unverified claim is labeled unverified, or it does not appear.**
Every row below carries its evidentiary basis. Nothing here should be repeated publicly
from the "indicated" or "reported" tiers without a direct load and a screenshot.

| Tier | Meaning |
|---|---|
| **Verified** | Loaded directly, or confirmed from the operator's own published page text |
| **Reported** | Observed by the operator in-session from screenshots; not independently re-verified in this repo |
| **Indicated** | Inferred from structure (routes, nav) — consistent with a conclusion but not proof of it |

> **Environment note.** `pierrereview.com` is blocked by this session's network egress proxy,
> so `/pricing` could not be loaded here. Direct verification of the paid tiers remains an
> open item and is assigned in §7.

---

## 2. What they have built — Verified

From their own published page text and district pages:

- Bill tracking for the South Dakota Legislature: live bill status, votes, legislator records
- **Statute diffs** — what a bill changes in existing law
- **Budget analysis** — department-level spending, "follow the money"
- **2026 election district pages** — e.g. `/s/2026/elections/state-house-4`,
  `/s/2026/elections/state-senate-19` — carrying per-candidate **party-loyalty percentages**
  (89%, 90% on the two districts sampled), sponsored-bill counts, and issue positions
- Bill search filterable by issue

**This last item is new information and changes the picture.** They are not confined to
legislative process data. They are already publishing candidate-comparison pages in an
election year. That is the same shelf a scorecard sits on.

## 3. What they have built — Reported

Observed in-session, not re-verified here:

- Interim committee transcripts
- Administrative rulemaking tracking
- Budget pages showing year-over-year department deltas: Corrections +8.4%, Health and Human
  Services +4.6%, Education −0.9% (state aid to education −1.7%), Public Utilities Commission
  +55.5%, Finance and Management +24.2%
- "88% party loyalty" as a displayed legislator metric *(consistent with the verified 89%/90%
  figures on the district pages)*

## 4. Monetization — Indicated, not established

- A `/pricing` route in the nav — **Indicated**
- An auth/login system — **Indicated**
- An `/integrations` page — **Indicated**

Three routes in that combination are the shape of a paid product with an API or export layer.
That is a reasonable inference and it is not a fact. **Do not write "Pierre Review charges $X"
anywhere public until §7.1 is closed.**

---

## 5. The actual strategic read

**They built the expensive, undifferentiated half of the product and are charging for it.**
Ingestion, normalization, statute diffing, vote records, budget category tables — that is most
of the engineering in the original Correspondence spec and none of its thesis. Rebuilding it
is the single worst use of the next six months.

**Their instrument is descriptive. It cannot ask the question ours exists to ask.**

Their budget pages report deltas with no normative floor. Every increase renders green and
every decrease renders red — which means "green" means only "went up." There is no
per-capita view, no inflation-adjusted baseline, no multi-year trendline, and above all no
question about whether a given line is a **proper object of state government at all**. A tool
built to be neutral between "Corrections +8.4%" and "PUC +55.5%" is structurally incapable of
the judgment the DOGE reviews already make. That gap is the whole product, and it is specified
in [`../method/budget-normalization.md`](../method/budget-normalization.md).

**Their scoring is descriptive; ours is normative — but the gap is narrower than it looks.**
The headline "88% party loyalty" is roll-call correlation: cheap, safe, and unfalsifiable as a
claim about anything, since a legislator can be 90% loyal to a caucus that is 90% wrong.
Underneath it, however, sits a real per-issue stance engine that is one weight vector away from
a normative scorecard. Benchmark conformance remains the metric nobody publishes, because a
declared benchmark invites the *"laundering your politics through dead men"* attack — but the
moat is the willingness to declare and cite a benchmark, **not** the difficulty of the
arithmetic. Full analysis in [`03-competitor-method-critique.md`](03-competitor-method-critique.md).

**They are state-only.** Nobody covers Watertown council, 14-4, or Codington County. Three DOGE
reviews and working scorecards already exist at that level. The same benchmark applied from
school board to statehouse is genuinely unoccupied — and it is the one lane where the operator
has standing rather than an opinion.

### The moat is a business-model constraint, not a technical one

State this precisely, because getting it wrong produces false comfort. Pierre Review is not
*unable* to build normative scoring. They are *unwilling*, because a declared benchmark forces
declared authorship, and declared authorship costs them the half of their market that buys
neutrality — lobby shops, agencies, press, and both caucuses. The moat holds exactly as long
as that constraint holds.

**Named risk:** the cheapest way for them to get normative coverage without paying the
authorship cost is to *host someone else's* — an existing scorecard from AFP, a Heritage
affiliate, or a state advocacy group — as an integration. Their `/integrations` page is where
that would appear. If a third-party conservative scorecard shows up on a Pierre Review
legislator page, the lane narrows sharply and the local-government tier becomes the only
defensible ground. This is the single indicator most worth watching.

---

## 6. The uncomfortable finding

The bake-off has sat staged since June. Pierre Review shipped a working product inside that
same window. The bottleneck was never model capability, ingestion architecture, or the choice
among three candidate builds — and adding a fourth build agent will not move it.

The viability gate is still unpassed: ten SD legislators, one axis, timed, human minutes per
dot placement. Until that number exists, every architecture decision downstream of it is
unfounded. Run it on a legal pad this week. See [`../../viability-gate/`](../../viability-gate/).

---

## 7. Open verification items

| # | Item | Method | Status |
|---|---|---|---|
| 7.1 | Pricing tiers and dollar figures | Load `/pricing` from an unblocked network; screenshot | Open |
| 7.2 | Whether `/integrations` offers an API or export usable as an input | Load `/integrations`; read terms | Open |
| 7.3 | Terms of service — automated access, reuse, and attribution rules | Load `/terms`; record verbatim | Open — **blocks any ingestion decision** |
| 7.4 | Whether party-loyalty scoring extends to issue-position scoring | Compare 3+ district pages | **Closed — yes.** 138-issue stance engine, see [`03`](03-competitor-method-critique.md) |
| 7.5 | Whether a third-party normative scorecard appears as an integration | Recheck quarterly | Open — trip-wire, see §5 |

Until 7.3 is answered in writing, no design assumes automated retrieval from their site.
The published-corpora path (LRC, SD Legislature site, county and municipal records) is the
load-bearing source and always was.

---

## Sources

- [Pierre Review — South Dakota Legislature Bill Tracker](https://pierrereview.com/)
- [State Senate District 4 | Elections | Pierre Review](https://pierrereview.com/s/2026/elections/state-senate-4)
- [State Senate District 19 | Elections | Pierre Review](https://pierrereview.com/s/2026/elections/state-senate-19)
- [State House District 4 | Elections | Pierre Review](https://pierrereview.com/s/2026/elections/state-house-4)
- [Search Bills | Pierre Review](https://pierrereview.com/s/2024/search?issue=reform+state+agency+operations)
- *How Issue Stance Scores Work*, Pierre Review blog, 2026-02-28, sdlegtracker.com — captured
  from operator screenshots 2026-09-02 (direct load blocked by this session's egress proxy)
