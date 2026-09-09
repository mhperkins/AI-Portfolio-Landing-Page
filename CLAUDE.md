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
| [index.html](index.html) | Main portfolio page — Shipped/Building/Workflow tabs, hero, contact, about |
| [composer-hub.html](composer-hub.html) | Deep-dive walkthrough of The Composition Hub (Compass + CRM + Virtual Agency) — screenshots, the piece life cycle, and a build-state matrix. Linked from the Composer Compass card on the Building tab. Written for the academic track. |
| [about.html](about.html) | Standalone About page — linked from nav |
| [resume.html](resume.html) | Resume page — renders the PDF in an iframe with a download button |
| [Software Developer Resume.pdf](Software Developer Resume.pdf) | Current resume, linked from resume.html |
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

| Tab | Content |
|---|---|
| Shipped | The Sprout Society Suite — CRM, Grant Assistant, Social Manager, Campaign Tracker |
| Building | The Composer Compass — tool scaffolded, agent training protocol active |
| Workflow | How I build tools (CLAUDE.md system, diff review) and how I build agents (intake form, rubric, experiment protocol) |

Each project card has: title, status tag, tech tags, Problem / Approach / Current Phase description.

---

## The Composition Hub walkthrough (`composer-hub.html`)

> Read this before iterating that page. Built 2026-09-09.

**What it is.** A deep-dive walkthrough of the whole Composition Hub (Composer's Compass + Composer
CRM + Virtual Agency), written for the **UW-Madison RISE-AI search committee**, not for dev
recruiters. The committee holds both this site's URL and maxwellhenrymusic.com, so the page must
corroborate the submitted cover letter rather than drift past it.

**Status: built and verified, committed, NOT pushed.** Production is unchanged until someone pushes.

### Structure and why it is shaped this way

| Zone | Contents | Reasoning |
|---|---|---|
| Always visible | Thesis line, cropped hub-cards image, the analytical question | A skimming committee member must reach these with zero clicks. Content behind an unclicked tab does not exist for them. |
| Tabs | Compass / CRM / Agency | The three tools are parallel alternatives, which is what tabs are for. Also mirrors `index.html` so the eventual merge is mechanical. |
| Carousel | The 8-stage life cycle, 3-up desktop / 1-up phone | The life cycle is a sequence, so it moves horizontally. Tabs for parallel, carousels for sequential. |
| Always visible | Closing "composer stays the author" argument | It is the thesis, not a detail. |

Do not move the analytical question or the thesis behind a tab. That was a deliberate call.

### Verified

Tabs switch; both carousels work (including the hidden-panel zero-width measurement bug, fixed by
dispatching `resize` on tab change); mobile is 1-up with no horizontal overflow at 390px; the print
stylesheet expands all three panels and hides the controls, because academics save pages as PDF;
zero console errors; zero em dashes.

### Next tasks, in priority order

1. **Add a Constitution and annotated-guide screenshot.** These are the strongest research evidence
   and the page currently only describes them. The constitution carries per-decision provenance,
   which is the most defensible artifact in the whole repo.
2. **Balance the tabs.** The Compass tab is far longer than CRM and Agency, which read thin.
3. **Decide on the build-state matrix.** Honest and good for an academic reader, but it is the most
   internal-engineering thing on the page.
4. **Then merge into `index.html`** (Max wants this folded into the Building tab, not left as a
   separate page). See below.

### The merge plan (agreed, not yet done)

`index.html` already runs two carousel systems: `carousel-slide` (half-width images, `aspect-video`,
used by the Sprout tools) and `section-carousel-slide` (full-width text, used by the Composer
Compass card). The Compass card has the text one but **no image carousel**.

`composer-hub.html` was deliberately built on the same tab-plus-carousel model, so merging is mostly
moving panel markup. The one reconciliation needed: it uses its own `car-*` classes and its own
initializer, which should be replaced with the existing `carousel-slide` markup and `index.html`'s
initializer. Two snags to solve when merging: the screenshots are 1.6:1 against `aspect-video`'s
1.78:1, and the canvas screenshot's node text becomes unreadable at half width.

### Accuracy constraints (do not loosen these)

Verified directly against the source repo. A committee may ask about any of it in an interview.

- **RAG is over score sidecars, not books.** `library/chroma_db` holds a `score_sidecars` collection
  with 17 entries. There is **no `theory_library` collection** and no `library/books/`. A stale claim
  on `index.html` ("semantic search over musicology texts") was corrected on 2026-09-09.
- **Numeric rubric scoring is deprecated.** No bass-fugue run was ever numerically scored. The
  two-run comparison document is the primary evaluation artifact. Never write "scored on a rubric."
- **The bass fugue is unfinished.** `scores/bass-fugue/drafts/` is empty; the only musical output is
  a validated 5-measure canon-subject sketch. The life cycle runs intake through first sketch.
- **MuseScore and Audiveris** are implemented and self-tested, but the external binaries were never
  installed, so they are "implemented," not "in use."
- **"My last three pieces"** is supportable as three pieces run through the same protocol, but they
  are not three equally complete case studies. Bass fugue has the fullest process record and the
  thinnest music; julies-suite has complete music but no constitution; piano-sonata has the most
  experimental depth and a finished draft but its constitution is archived, not current.

### Re-capturing screenshots

Full procedure in `Composition_Hub_Tool/composers-compass/docs/deliveries/2026-09-09/README.md`.
Essentials: run `cd app-ui && npm run dev` (fixed port 5173), seed the Compass piece via
`/seed-bass-fugue.html`, write `compass:contact:*` / `compass:org:*` / `compass:concert:*` keys
directly for the CRM, and set `compass:__lastexport__` so the hub header does not read "Never backed
up." Capture with Playwright at `deviceScaleFactor: 2`.

**Never screenshot the real CRM.** It holds real contacts' names and email addresses and these
images are published publicly. Always use clearly fictional sample records.

---

## Status Tags

```
.status-live    green    — deployed and actively used in production
.status-mvp     yellow   — functional but not in active production use
.status-wip     purple   — actively being built
```

---

## Current Portfolio State (September 2026)

This site is served from its Vercel default domain (ai-portfolio-landing-page.vercel.app). No custom domain is attached to it.

All major items from the previous Known Updates list are resolved:
- Headline updated to output-focused language ("I build AI-assisted tools, not prototypes.")
- About page exists (about.html) and About section on index.html
- Problem/solution/outcome framing on all project cards
- Social Manager moved to Shipped tab
- The Composer Compass added to Building tab with full training protocol description
- Workflow tab updated with agent training methodology paragraph

**Remaining on the site itself:**
- Loom for Social Media Manager V2 needs to be recorded
- Workflow tab Loom needs to be redone to show the composition training protocol

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
