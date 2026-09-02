# Coverage Map — Where They Are, Where They Aren't, and Which Gaps Are Protected

**Prepared:** September 2026
**Sources:** Pierre Review *Election Coverage: Applying Voting Records to Candidates* (blog,
April 14, 2026, sdlegtracker.com) and site structure — captured from operator screenshots
2026-09-02; operator observation of update cadence.

---

## 1. What the April 2026 election post adds — Verified (their own words)

- **"Same methodology that powers our legislator scores, now applied to everyone on the 2026
  ballot."** Elections index for every 2026 race, grouped by office, with contested-primary flags.
- **Race pages:** candidates separated by primary, side-by-side issue-stance comparison,
  endorsements, campaign finance (FEC for federal, state filings for state).
- **Governor's record panel:** every bill signed or vetoed, *"with the political direction of
  each action."*
- **Congressional stances:** candidates who hold or recently held federal office are scored
  from their US House or Senate record, on the same issue categories, with the source labeled.
- **Endorsement alignment:** where an endorser has a voting record, they compute how closely it
  aligns with the endorsed candidate's positions.
- **Their thin-record rule, stated:** *"One thing we don't do: invent a score for a candidate
  with no prior voting record… we'd rather show nothing than guess. You'll see the other
  candidates in the race scored and that candidate left blank — that's intentional."*

**Credit this plainly.** That last rule is the civic-scorecard thin-record rule, and they
state it better than most advocacy scorecards ever have. It partially answers Q4 in
[`03-competitor-method-critique.md`](03-competitor-method-critique.md) for the *no-record*
case. It does not answer it for the *thin-record incumbent* — one relevant vote still displays
at full magnitude — and that distinction is where our `—` marker still earns its place.

**Two smaller observations, Verified from the captures:**
- Several image embeds in both blog posts render as broken (placeholder icons) as of
  September 2026, five to seven months after publication.
- "Political direction of each action" is their phrase. It concedes, in their own copy, that
  the instrument assigns a political direction — which is the frame §4 of the method critique
  says is undeclared. Quote it when the point needs making.

## 2. Update cadence — Indicated, not established

The operator's read: no live editorial or agentic layer updating the site beyond recurring
scrapes of legislative activity. Consistent signals: broken images unrepaired for months, a
blog cadence of roughly one post per six weeks, and content whose freshness tracks the
legislative calendar rather than the news cycle.

**This is an inference from surface signals and must stay labeled as one.** It is probably
right, and it would be a mistake to build on it as if it were verified. A small team with a
working scraper can add a new source in weeks if the source is machine-readable. That
qualifier — *if the source is machine-readable* — is the entire strategic point of §3.

## 3. The coverage matrix

The question for each row is not "do they cover it" but **"if they wanted to, what would stop
them?"** A gap that only exists because nobody has bothered is a lane that closes the day
someone bothers. A gap that exists because the underlying data is ugly is a lane a
scrape-first competitor cannot enter without hiring people — which is the thing their
architecture exists to avoid.

| Body / level | Them (Sept 2026) | Data shape | Gap type | Our standing |
|---|---|---|---|---|
| **SD Legislature** — bills, votes, statute diffs | Full | LRC, structured, machine-readable | *Occupied* | None on descriptive; normative only |
| **SD federal delegation** — roll calls | Scored on their taxonomy | Congress.gov, structured | *Occupied* (descriptive) | Normative only; within the structural fence |
| **Governor** — signed/vetoed | Record panel | Structured | *Occupied* | Normative only |
| **Campaign finance** | FEC + state filings | Structured | *Occupied* | None |
| **Public Utilities Commission** — dockets, orders | **None** | puc.sd.gov dockets are online; filings are PDFs; orders are semi-structured | **Unoccupied, NOT protected** | Subject-matter standing (eminent domain, siting, rate cases — the live A4 property-and-contract axis in this state) |
| **State boards & commissions** — appointed, rulemaking | Rulemaking tracked (reported); boards themselves not | Mixed; agendas/minutes as PDFs | **Unoccupied, partly protected** | Normative (A2: proper object; A6: process and consent) |
| **County commissions** (66) | **None** | Minutes as PDFs or scans; no uniform schema; some counties paper-only | **Unoccupied, PROTECTED** | **Direct** — Codington County review exists |
| **City councils** | **None** | Same as counties; worse in small towns | **Unoccupied, PROTECTED** | **Direct** — Watertown reviews, 14-4 record |
| **School boards** (~150 districts) | **None** | Board packets as PDFs; budget documents non-uniform | **Unoccupied, PROTECTED** | **Direct** — scorecards exist in draft |
| **Planning & zoning, townships, special districts** | **None** | Frequently not online at all | **Unoccupied, PROTECTED** | Local standing |

### Reading the matrix

- **The bottom four rows are the product.** They are unoccupied, they are protected by the
  shape of the data, and they are where the operator has standing rather than an opinion.
  A scrape-first competitor cannot follow without human readers, and human readers are what
  hand-scored artifacts already are.
- **PUC is the trap row.** It looks like the local rows — nobody covers it, the subject matter
  is exactly where a property-and-contract benchmark bites hardest in South Dakota — but its
  dockets are online and a competent scraper could be pointed at them in a month. Treat PUC as
  a *second* lane, entered with normative artifacts that are hard to copy, not as ground that
  will stay empty.
- **The top four rows are consumed, not contested.** Nothing in this repo rebuilds them.

## 4. What this changes

1. **The first scored artifacts are local.** Not legislature. The viability gate still runs on
   ten legislators, because A2 on the statehouse is the hardest honest test of the *method* —
   but the first *published* artifacts go where the lane is protected: county, council, school
   board.
2. **PUC gets a normative artifact early**, while the row is still empty, because the row will
   not stay empty and a published, cited artifact is the only claim on it that survives a
   scraper arriving.
3. **Do not build on "they have no live agents."** Build on "their coverage is bounded by
   machine-readable sources." The second is durable; the first is a reading of a blog's image
   tags.

## Verification items added

| # | Item | Status |
|---|---|---|
| 4.1 | Confirm rulemaking coverage exists (was Reported, not Verified) | Open |
| 4.2 | Confirm no PUC docket coverage by site search | Open |
| 4.3 | Re-check in 90 days whether local or PUC coverage has appeared | Open — trip-wire |
