# Build Plan — In Plain Terms

**Who does what, in what order.** Written for the operator, not for an engineer.

---

## First, what their site actually is

Their menu: **Dashboard · Bills · Legislators · Committees · Budget · Elections · Search · Blog.**
Their pinned welcome post is dated **February 28, 2026** — the site is about six months old.

Underneath those eight tabs are three things:

1. **A scraper** that pulls bills, votes, and budget tables from the Legislative Research
   Council's website on a schedule.
2. **A database** that stores what the scraper found.
3. **A website** that shows the database, with a login.

That is a real engineering project. It is also the part of the product that has no thesis in
it. You are not building it. Here is what each of their tabs maps to for you:

| Their tab | What it is for you | Build it? |
|---|---|---|
| Blog | **Your methodology page** — the frames, the scale, the lenses, the authorship disclosure | **Yes — first** |
| Budget | **Four Lenses** — already drafted in `builds/` | **Yes — after you supply the primary document** |
| Legislators | **The scorecard** | **Only after the gate passes** |
| Elections | Scored candidates | Later, only as artifacts |
| Bills, Committees, Search, Dashboard | Their infrastructure | **No.** Link to the LRC, or to them. |

---

## The stack, in one paragraph

Your site is **a folder of HTML files.** GitHub serves that folder for free at a public
address (GitHub Pages) — no server, no database, no login, nothing to maintain, nothing that
goes down at 2 a.m. Claude Code writes the files and pushes them; the site updates itself when
the push lands. If the gate passes and the scorecard becomes interactive, the same folder
gains a JavaScript file and a data file. Still no server. A database and a scraper enter the
picture only if you ever decide to cover the full legislature every session automatically —
and that decision is months away and gated.

---

## The division of labor

The line is simple: **Claude Code does everything that is text, arithmetic, files, and
plumbing. You do everything that is judgment, access, or signature.**

### Only you can do these

| # | Task | Why it has to be you | Time |
|---|---|---|---|
| Y1 | **Run the viability gate** on a legal pad — `viability-gate/tally-sheet.md` | It measures *your* minutes per placement. Nobody else's number means anything. | One sitting + 48 h re-score |
| Y2 | **Download the primary documents** and put them in `sources/` | Some state sites are unreachable from Claude Code's network. Your phone or laptop can reach them. | 30 min |
| Y3 | **Verify the roster** from the LRC or Secretary of State and initial the sheet | A roster error invalidates everything. The rule says a human confirms it. | 20 min |
| Y4 | **Make every L4 call** — governmental / gray / fraught — on every line | This is the normative judgment. It is the product. Claude drafts a proposed call; you decide. Human-in-the-lead is your own commitment. | 10–15 min per artifact |
| Y5 | **Reconcile the five frame rationales** against spec v0.3 | The spec lives with you, not in this repo. | 20 min |
| Y6 | **Load `/pricing` and `/terms` on their site** on your own network; screenshot into `sources/competitor/` | Blocked from here. Terms decide whether their data is ever an input. | 10 min |
| Y7 | **Pick the friendly subject who gets an unflattering score** | Nobody can choose this for you, and the instrument is a campaign tool without it. | A decision |
| Y8 | **Turn on GitHub Pages** — repo Settings → Pages → Build and deployment → Source: **GitHub Actions** | One click that requires your GitHub login. The workflow in `.github/workflows/pages.yml` does the rest on every push to `main`. | 2 min |
| Y9 | **Sign each artifact** before it publishes | Owned authorship means a name on it. | Read time |

### Claude Code does these

| # | Task | Depends on |
|---|---|---|
| C1 | Extract tables from the primary PDFs, cite by page, re-derive every figure on the Four Lenses page, flip its tier from Reported to Verified | Y2 |
| C2 | Build the **methodology page** from `docs/method/` — plain-language, phone-readable, authorship on top | **Done** — `site/methodology.html` |
| C3 | Build the **site shell**: home, methodology, artifacts index, sources — static HTML in the house tokens | **Done** — `site/` |
| C4 | Draft the **first local artifact** (Watertown FY2026 review is already written; port it into the same four-lens frame) | Y2 (the adopted budget) |
| C5 | Build the **scorecard renderer**: you fill a spreadsheet (subject, axis, band, citation, reason); it renders the table, the gap column, and the could-not-verify section | Y1 result |
| C6 | Draft proposed L4 calls, questions, and could-not-verify sections for each artifact — for you to edit | C1 / C4 |
| C7 | Set up the repo so a push publishes the site automatically | **Done** — workflow committed; activates on Y8 and a merge to `main` |
| C8 | *Gated:* write a fetcher for LRC bill and vote data (the LRC site serves its own pages from public JSON) | Gate PASS **and** terms read |
| C9 | *Gated:* the interactive matrix | Gate PASS |

---

## The sequence

### Week 1 — decide whether this is a product
- **You:** Y1 (the gate), Y2 (documents), Y3 (roster), Y6 (their pricing/terms).
- **Claude Code:** C2, C3 — the methodology page and site shell, in parallel, needing nothing from you.
- **End of week:** a number in `viability-gate/RESULT.md`, and a site shell you can open on your phone.

### Week 2 — make the first thing true
- **You:** Y4 on the Four Lenses page and the Watertown port; Y5.
- **Claude Code:** C1, C4, C6. The Four Lenses page goes from Reported to Verified with page citations.
- **End of week:** two artifacts you would put your name on. Not yet published.

### Week 3 — publish
- **You:** Y7, Y8, Y9.
- **Claude Code:** C7. The site goes live with: methodology, Four Lenses (verified), one local artifact.
- **End of week:** a URL. Three pages. Every number traceable.

### After that — the gate decides
| Gate result | What happens |
|---|---|
| **PASS** | C5 → C8 → C9, in that order. The bake-off finally has a reason to run. |
| **CONDITIONAL** | C5 only. Three to five hand-scored artifacts. Re-gate after they ship. |
| **FAIL** | No scorecard build. Local fiscal reviews, done well, are the product. Re-run the gate once with a tightened axis. |

---

## What you never have to do

- Write code, HTML, or CSS.
- Run a server, buy hosting, or manage a database.
- Build ingestion, search, bill tracking, or committee pages.
- Match their eight tabs. Three pages that are unimpeachable beat eight that are commodity.

## What Claude Code never does without you

- Score a person.
- Assign an L4 category as final.
- Publish.
- Take a dependency on a third-party site whose terms you haven't read.

---

## The one thing to do today

Print `viability-gate/tally-sheet.md`. Sign the thresholds. That's it. Everything else in this
plan is downstream of a number that only you can produce.

---

## Network access for Claude Code sessions

This is **not a repo setting.** It is configured once at claude.ai/code → Environments →
this repo's environment → Network access. A repo cannot grant itself network access.

Choose **Full**, or choose **Limited** and paste this allowlist, one host per line:

```
sdlegislature.gov
bfm.sd.gov
open.sd.gov
sdsos.gov
doe.sd.gov
watertownsd.us
codington.org
watertown.k12.sd.us
founders.archives.gov
avalon.law.yale.edu
loc.gov
api.bls.gov
api.census.gov
pierrereview.com
sdlegtracker.com
```

No API keys are required for any host on this list. BLS and Census answer keyless at low
volume; a free key only raises the daily limit.

Until this is set, Claude Code cannot fetch from any state source, and the workaround is
Y2 in the plan: download the PDFs yourself and place them in `sources/`.
