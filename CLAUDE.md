# AI Tool Portfolio — CLAUDE.md

> Project memory and context for Claude Code. Not committed to git.

---

## What This Is

Max's personal portfolio site. Static HTML — no build step, no bundler, no framework. Push to git and Vercel deploys automatically.

**Live at:** https://ai-portfolio-landing-page.vercel.app/
Vercel project: `ai-portfolio-landing-page` · GitHub: `mhperkins/AI-Portfolio-Landing-Page`

> **Not to be confused with the composer portfolio.** maxwellhenrymusic.com and the
> `composer-portfolio` Vercel project belong to a *different* site, whose source lives at
> `Composition_Hub_Tool/composers-compass/portfolio/site/`. Never deploy this repo to that
> project. See that project's CLAUDE.md for its own deploy pipeline (`sync.mjs`).

---

## Architecture

| Layer | Detail |
|---|---|
| Stack | Plain HTML, Tailwind CSS (CDN), custom CSS in `<style>` tags |
| Fonts | Inter, JetBrains Mono, Barlow Condensed — loaded via Google Fonts |
| Deployment | Vercel — auto-deploys on push to main |
| No build step | No npm, no bundler, no compile step |

---

## Files

| File | Role |
|---|---|
| [index.html](index.html) | Main portfolio page — **The Composer Hub / Sprout Society Suite** tabs, hero, contact, about. The Hub tab holds the whole Composer Hub walkthrough (merged in 2026-09-09). |
| [composer-hub.html](composer-hub.html) | **Retired 2026-09-09 — now a redirect** to `index.html#composition`. Kept, not deleted, because the old public URL may have been shared in an academic application. |
| [about.html](about.html) | Standalone About page — linked from nav |
| [resume.html](resume.html) | **CV page** — the academic CV rendered as a native page (was a PDF iframe until 2026-09-09). Has a print stylesheet and a DOCX download. |
| [Software Developer Resume.pdf](Software Developer Resume.pdf) | Software track resume. **Currently unlinked** — nothing routes to it since resume.html became the academic CV. |
| [Academic CV - UW Madison.docx](Academic CV - UW Madison.docx) | Source of the CV page; offered as the download on resume.html |
| [images/](images/) | Screenshots and assets |
| [career-search-handoff.md](career-search-handoff.md) | Snapshot of career search status — context for Claude sessions |
| [career-search-master.md](career-search-master.md) | AI/dev track — full ongoing career strategy document |
| [career-search-ops-track.md](career-search-ops-track.md) | Arts/nonprofit operations track — hard rules, story, proof points, application log |
| [career-search-academic-track.md](career-search-academic-track.md) | Academic music technology & AI track — hard rules, story, proof points, application log |
| [Operations Resume.md](Operations%20Resume.md) | Resume draft for the ops track (do not send the dev PDF on this track) |
| [Academic CV - UW Madison.md](Academic%20CV%20-%20UW%20Madison.md) | Academic CV draft for the UW-Madison RISE-AI posting |
| [Academic Cover Letter - UW Madison.md](Academic%20Cover%20Letter%20-%20UW%20Madison.md) | Cover letter draft for the same posting |
| [Teaching Statement - UW Madison.md](Teaching%20Statement%20-%20UW%20Madison.md) | Required teaching statement for the same posting |

---

## Coding Conventions

- **No build tooling.** Do not add npm, webpack, Vite, or any build step. Everything runs directly in the browser.
- **Tailwind via CDN.** The `tailwind.config` script block at the top of each file extends the default theme. Do not install Tailwind as a package.
- **Custom CSS lives in `<style>` tags** in the `<head>` of each file. Use Tailwind utility classes for layout and spacing; use the `<style>` block for animations, custom component classes (`.card-hover`, `.tag`, `.status-live`, etc.), and anything Tailwind can't express cleanly.
- **No JavaScript frameworks.** Vanilla JS only, inline in `<script>` tags at the bottom of the body.
- **One file per page.** index.html, about.html, and resume.html are self-contained. Do not split into partials or components.
- **No em dashes.** Use commas, periods, or restructure the sentence.

---

## Deployment

Push to main. Vercel picks it up automatically. No build command, no output directory to configure — Vercel serves the files directly.

To test locally: open `index.html` in a browser, or run `npx serve .` if you need a local server for relative path testing.

---

## Portfolio Structure (index.html)

The page has tabbed sections. The sticky tab nav sits outside the hero section so it persists through the full page scroll.

| Tab | id | Content |
|---|---|---|
| The Composer Hub | `tab-hub` | Composer Compass, Composer CRM, Virtual Agency as three sub-tabs, then the component table. Default tab. |
| Sprout Society Suite | `tab-sprout` | CRM, Grant Assistant, Social Manager, Campaign Tracker as four sub-tabs |

Tabs are named for their **subject, not their status**. "Shipped / Building" was the old axis and
it filed the Hub under unfinished. Do not go back to it. Workflow was removed on 2026-09-09 and
will be rebuilt later; `#tab-workflow` and `#tab-progress` both resolve to `tab-hub` meanwhile.

Each project card has: title, status tag, tech tags, Problem / Approach / Current Phase description.

---

## The Composer Hub (the first tab of `index.html`)

> Read this before iterating it. Built 2026-09-09 as a standalone page, merged into
> `index.html` the same day.

**What it is.** A deep-dive walkthrough of the whole Composer Hub (Composer Compass + Composer
CRM + Virtual Agency), written for the **UW-Madison RISE-AI search committee**, not for dev
recruiters. The committee holds both this site's URL and maxwellhenrymusic.com, so the page must
corroborate the submitted cover letter rather than drift past it.

**Status: merged into `index.html` and live-verified, NOT pushed.** Production is unchanged
until someone pushes.

### Structure and why it is shaped this way

| Zone | Contents | Reasoning |
|---|---|---|
| Suite banner | Name, the three tool names, three framing lines | Mirrors the Sprout tab so both read as one design |
| Sub-tabs | Compass / CRM / Agency | Three parallel tools, which is what tabs are for |
| Per tool | Title, subtitle, tech tags, **three benefit cards**, a heading, then the annotated screenshot or carousel | The cards answer "why does this matter" before the screenshot answers "what does it look like". Max wrote all nine card texts. |
| Shared, below the sub-tabs | The component table only | It describes hub-wide infrastructure rather than one tool |

The page is deliberately near-prose-free. Earlier drafts had paragraph intros on every tab and an
eight-card life-cycle carousel with no image at all; Max cut all of it on 2026-09-09. Bullets and
pinned screenshots only. Do not reintroduce explanatory paragraphs.

### Verified (after the merge, headless)

Tabs and both sets of sub-tabs switch, and switching a Hub tool no longer disturbs Sprout's state;
both Hub carousels advance and report `01 / 02` and `01 / 03`; the arrows sit fully outside the
image with their centre exactly on the image centre (dy = 0); the canvas renders at ratio 1.600
with pin 3 landing at 57% / 30.9% against 57% / 31% authored; no broken images; zero script errors;
zero em dashes. `#tab-progress`, `#tab-workflow`, `#composition` and `composer-hub.html` all still
land on the Hub.

Note: the page makes ~2100 requests with ~700 failures on load, from the Loom iframes retrying.
That is pre-existing and identical before and after the merge; it is not caused by the Hub images.

### Open items

1. **The chaconne slide has no overlay callouts yet.** Slide 2 of the Compass carousel is the
   score for *Chaconne for Bass and Pedal Board*. It sits in a forced 16:10 frame, which leaves
   roughly 250px of dark margin either side specifically for callouts. Max is writing the text.
2. **A Constitution / annotated-guide screenshot** would be the strongest research evidence and
   is still only described, never shown.
3. **`Software Developer Resume.pdf` is unlinked.** Decide whether the software track needs its
   own route (`resume-dev.html`) alongside the academic CV.
4. **"The composer stays the author" is unused.** It was the heading over the shared card block
   before the cards went per-tool. Strongest line on the page; natural home is above the Compass
   cards.
5. **Rebuild the Workflow tab** when there is something worth putting in it.

### The merge (done, 2026-09-09)

Folded into `index.html` as the **first tab**, replacing the old "Building" tab. The tabs went
from a status axis (Shipped / Building / Workflow) to a project axis (The Composer Hub /
Sprout Society Suite), which also stops the Hub being filed under "not finished".

It mirrors the Sprout tab exactly: suite banner, three `tool-btn` sub-tabs, one card per tool,
then the shared argument and component table. No nested tab row.

Four things a future session needs to know before touching it:

1. **The annotated screenshots must stay full width and 16:10.** Pins are positioned as
   percentages of the image box and sized in `cqw`. A half-width card renders the pin labels at
   about 5.6px, and any ratio other than the images' true 1.6 makes `object-fit` letterbox the
   image, which slides every pin off the thing it points at. This is why they do **not** reuse
   the half-width `carousel-slide` / `aspect-video` system.
2. **The Hub carousels are a separate system on purpose.** They use `data-hub-carousel` and a
   `hub-car-*` class prefix with their own initializer. `initCarousels()` expects `.carousel-*`
   children and throws on a null prev button if it matches Hub markup.
3. **`switchTool()` is scoped to the clicked button's `.tab-panel`.** Two tabs now run sub-tabs;
   unscoped, switching a Hub tool blanked every Sprout panel.
4. **Old entry points still resolve.** `#tab-progress` maps to `tab-hub` in `cardToTab`, and
   `composer-hub.html` is a redirect. Do not delete either shortcut.

### Accuracy stance (set by Max, 2026-09-09)

This tool has exactly one user: Max. The portfolio exists to demonstrate what he can make it do,
so **small gaps between a claim and the current repo state are acceptable** and should not be
chased. The rule is narrower than it used to be:

> Any discrepancies are fine, as long as the portfolio does not *highlight* discrepancies.

So do not write the caveat into the page. Earlier drafts volunteered "the binaries were never
installed", "numeric scoring was deprecated", "built but idle", "retired unrun" and "the fugue is
in progress"; all of that was removed on 2026-09-09 because it undercut the demo without being
asked for. Describe capability, do not audit it.

Two things that are **not** caveats and must stay:

- **CRM screens use fictional sample records.** That line stays in the page footer. It is what
  stops a reader assuming the sample names are real people, and it is what makes showing those
  screens acceptable at all.
- **Never screenshot the real CRM.** It holds real contacts' names and email addresses and these
  images are published. Seed fictional data instead; the procedure is in the Compass repo at
  `docs/deliveries/2026-09-09/README.md`.

## Status Tags

```
.status-live    green    — deployed and actively used in production
.status-mvp     yellow   — functional but not in active production use
.status-wip     purple   — actively being built
```

---

## Current Portfolio State (September 2026)

This site is served from its Vercel default domain (ai-portfolio-landing-page.vercel.app). No custom domain is attached to it.

### Session of 2026-09-09 (large restructure, NOT pushed)

Everything below is on disk and live-verified headless, but **uncommitted on `main`**. Production
is unchanged until someone commits and pushes.

**The site is now two tabs, named for their subject rather than their status.**

| Tab | id | State |
|---|---|---|
| The Composer Hub | `tab-hub` | Default. Suite banner, three tool sub-tabs, then the component table. |
| Sprout Society Suite | `tab-sprout` | Unchanged: four tool sub-tabs. |

- **Shipped / Building / Workflow are gone.** "Shipped/Building" was a status axis that filed the
  Hub under unfinished. **Workflow was removed entirely on 2026-09-09** — Max will rebuild it
  later. Its 54 lines are recoverable from commit `8b46ee0` and the panel is not commented out.
- Stale hashes still resolve: `#tab-progress` and `#tab-workflow` both map to `tab-hub`, and
  `composer-hub.html` is a redirect rather than a deletion. Do not remove those shortcuts.

**The Composer Hub tab** (was the standalone `composer-hub.html`, merged the same day):

- Named **"The Composer Hub"**, and the tool is **"Composer Compass"** with no apostrophe. Renamed
  from "Composition Hub" / "Composer's Compass" late in the session; this matches the CV.
- Each of the three tools is: title + subtitle + tech tags, **three benefit cards**, a heading, then
  an annotated screenshot or carousel. The cards are per-tool and Max wrote all nine.
- The old shared "The composer stays the author" block is retired; its three cards became the
  Compass set. **That heading is currently unused** and is the strongest line on the page, so it
  is worth reinstating above the Compass cards if there is ever a reason.
- `images/Hub_Cards.png` was removed from the page (still on disk, unreferenced). It showed the
  old "Composer's Compass" spelling, so removing it also resolved the last naming mismatch.

**Screenshots.** All Hub screenshots carry numbered pills that name what they point at. The app's
own UI text renders around 4px at page width, so the pills are the readable layer, not a duplicate.
Two CRM screens were re-captured on 2026-09-09 because the originals showed empty states: the
Groove Theory II concert page and the newsletter editor. Seeding procedure and shapes are in the
Compass repo at `docs/deliveries/2026-09-09/README.md`.

**The CV replaced the resume.** `resume.html` is now the academic CV as a native page with a print
stylesheet, not a PDF iframe. Nav reads "CV" everywhere. `Software Developer Resume.pdf` is on disk
but **unlinked** — decide whether the software track needs its own route.

**Known, checked, and deliberately left alone** (both pre-existing, identical in the pre-merge
backup, neither caused by this work):
- The page makes ~2100 requests with ~700 failures on load, from the Loom iframes retrying.
- Horizontal overflow at 390px, caused by the hero `H1` reaching 426px.
- Pin labels scale with the image, so on a 390px phone they render ~3.4px. A font floor would make
  the pills collide; solve it deliberately or not at all.

**Remaining on the site itself:**
- Loom for Social Media Manager V2 needs to be recorded
- The chaconne score slide (Compass carousel, slide 2) has no overlay callouts yet; Max is writing
  them. It sits in a forced 16:10 frame leaving ~250px of dark margin either side for exactly that.
- Rebuild a Workflow tab when there is something worth putting in it

**Career search has expanded to three parallel tracks (as of Sept 2026):**
1. **AI/dev track** (`career-search-master.md`) — original track, unchanged.
2. **Arts/nonprofit operations track** (`career-search-ops-track.md`) — AI/portfolio disclosure
   rule changed from a blanket ban to case-by-case: still omitted by default for traditional arts
   ops roles, but surfaced when the org or role is itself tech- or AI-adjacent.
3. **Academic music technology & AI track** (`career-search-academic-track.md`, new) — tenure-track
   and academic postings at the intersection of music, tech, and AI. First target: UW-Madison
   Mead Witter School of Music, Assistant Professor of Music Technology and AI (RISE-AI),
   requisition JR10004513. **Application submitted September 9, 2026** (CV, cover letter, teaching
   statement) with The Composer Compass as the focal creative/research work. Framing leans into
   practical builder experience as a legitimate primary qualification for a field with no
   established academic pipeline yet, not an apology for lacking a doctorate.

**Next task (as of Sept 9, 2026):** primary focus shifts back to the arts/nonprofit operations
track (`career-search-ops-track.md`) — a different strategy from the academic one, applying to
general arts admin roles on an ongoing basis. The academic track continues in parallel and
opportunistically: watch for other postings similar to RISE-AI and apply under the same framing.

---

## Career Context

Targeting: AI developer, junior full-stack, and internal tools roles on the primary track. Not "vibe coder" framing.

The Sprout Suite (CRM + Grant Assistant + Social Manager + Campaign Tracker) is the portfolio centerpiece — four interconnected tools for one real nonprofit, one Supabase backend, actively used in production. Frame as a system, not a list.

The MCP server and The Composer Compass training protocol are the strongest technical differentiators for AI dev roles specifically. The MCP server shows Claude API tool use with real data. The training protocol shows rubric design, structured evaluation, and agent architecture thinking — not just "I called the API."

The Workflow tab is the section most worth investing in. The current copy is solid. The Loom is the weak link — it needs to show intentional methodology, not blind Claude use.

The Composer Compass has grown beyond a portfolio project: it is now also the centerpiece of the academic track's application materials, framed there as an independent research/evaluation project rather than a dev-portfolio tool.
