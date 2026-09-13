# AI Tool Portfolio — CLAUDE.md

> Project memory and context for Claude Code. **Tracked in git** (committed alongside the page
> through `f3fc9fa`), so an update here needs a commit and push like any other file.

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
| [index.html](index.html) | Main portfolio page: **The Composer Hub / TeacherAID / Sprout Society Suite** tabs, hero, contact, about. The Hub tab holds the whole Composer Hub walkthrough (merged in 2026-09-09). |
| [composer-hub.html](composer-hub.html) | **Retired 2026-09-09 — now a redirect** to `index.html#composition`. Kept, not deleted, because the old public URL may have been shared in an academic application. |
| [about.html](about.html) | Standalone About page — linked from nav |
| [resume.html](resume.html) | **CV page** — the academic CV rendered as a native page (was a PDF iframe until 2026-09-09). Has a print stylesheet and a DOCX download. |
| [Software Developer Resume.pdf](Software Developer Resume.pdf) | Software track resume. **Currently unlinked** — nothing routes to it since resume.html became the academic CV. |
| [Academic CV - UW Madison.docx](Academic CV - UW Madison.docx) | Source of the CV page; offered as the download on resume.html |
| [demo/compass-demo.html](demo/compass-demo.html) | **Iteration source for the Compass panel's carousel** (built 2026-09-09, transplanted 2026-09-10). Change slides here, then re-transplant. See "The Compass demo carousel" below. |
| [demo/crm-demo.html](demo/crm-demo.html) | **Iteration source for the CRM panel's carousel** (7 slides, transplanted 2026-09-10). See "The CRM and Agency carousels" below. |
| [demo/agency-demo.html](demo/agency-demo.html) | **Iteration source for the Virtual Agency panel's carousel** (2 slides, transplanted 2026-09-10). |
| [demo/dasha-demo.html](demo/dasha-demo.html) | **Iteration source for the TeacherAID tab's carousel** (6 annotated slides, transplanted 2026-09-12). See "The TeacherAID tab" below. |
| [demo/sprout-crm-demo.html](demo/sprout-crm-demo.html) | **Iteration source for the Sprout CRM panel's carousel** (5 annotated slides; built by a parallel session, committed `6c226cc`, transplanted 2026-09-12). See "The Sprout CRM carousel" below. |
| [demo/grant-demo.html](demo/grant-demo.html) | **Iteration source for the Grant Finder panel's carousel** (6 annotated slides, transplanted 2026-09-12). See "The Grant, Social and Campaign carousels" below. |
| [demo/social-demo.html](demo/social-demo.html) | **Iteration source for the Social Planner panel's carousel** (5 annotated slides, transplanted 2026-09-12). |
| [demo/campaign-demo.html](demo/campaign-demo.html) | **Iteration source for the Campaign Tracker panel's carousel** (5 annotated slides, transplanted 2026-09-12). |
| [demo/assets/](demo/assets/) | Carousel assets: `chaconne-p1.webp` (copied from the composer portfolio's score previews) and `chaconne-excerpt.mp3`, the 45-second cut from 8:25 of the Chaconne recording that slide 5 plays in both copies. |
| [images/](images/) | Screenshots and assets |
| [career-search-handoff.md](career-search-handoff.md) | Snapshot of career search status — context for Claude sessions |
| [career-search-master.md](career-search-master.md) | AI/dev track — full ongoing career strategy document |
| [career-search-ops-track.md](career-search-ops-track.md) | Arts/nonprofit operations track — hard rules, story, proof points, application log |
| [career-search-academic-track.md](career-search-academic-track.md) | Academic music technology & AI track — hard rules, story, proof points, application log |
| [career-search-arts-education-track.md](career-search-arts-education-track.md) | Arts nonprofit community engagement & education sub-track of the ops track. Current State section at the top; holds the WCO letter, application answers, and research notes |
| [Operations Resume.md](Operations%20Resume.md) | Resume draft for the ops track (do not send the dev PDF on this track) |
| [Community Engagement Resume.md](Community%20Engagement%20Resume.md) | Text source for the arts-education resume, in the academic CV's format |
| [Maxwell Perkins Resume - Community Engagement.pdf](Maxwell%20Perkins%20Resume%20-%20Community%20Engagement.pdf) | **The file to send** on the arts-education track (one page; `.docx` beside it). Not committed as of 2026-09-10 |
| [build_resume.py](build_resume.py) | Rebuilds that `.docx` with python-docx, using `Academic CV - UW Madison.docx` as the style template. Export the PDF through Word. Not committed as of 2026-09-10 |
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

**End-of-session protocol (Max's rule): update Current State, then commit and push to `main`
without waiting to be asked.** Vercel only builds production on a push, so a session that ends
on preview deploys leaves the live site behind. Stage named files, never `-A`.

Push to main. Vercel picks it up automatically. No build command, no output directory to configure — Vercel serves the files directly.

To test locally: open `index.html` in a browser, or run `npx serve .` if you need a local server for relative path testing.

---

## Portfolio Structure (index.html)

The page has tabbed sections. The sticky tab nav sits outside the hero section so it persists through the full page scroll.

| Tab | id | Content |
|---|---|---|
| The Composer Hub | `tab-hub` | Composer Compass, Composer CRM, Virtual Agency as three sub-tabs, then the component table. Default tab. |
| TeacherAID | `tab-dasha` | One tool, no sub-tabs: suite banner, one card (tags, three benefit cards, heading), the annotated carousel. Added 2026-09-12. |
| Sprout Society Suite | `tab-sprout` | CRM, Grant Assistant, Social Manager, Campaign Tracker as four sub-tabs. All four panels are annotated carousels as of 2026-09-12; no Sprout panel uses a Loom or screenshots now. |

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

**Status: live.** Pushed 2026-09-10. All three panels are HTML carousels now; no Hub panel uses a
screenshot. Commit trail is under "Session of 2026-09-10" in Current Portfolio State.

### Structure and why it is shaped this way

| Zone | Contents | Reasoning |
|---|---|---|
| Suite banner | Name, the three tool names, three framing lines | Mirrors the Sprout tab so both read as one design |
| Sub-tabs | Compass / CRM / Agency | Three parallel tools, which is what tabs are for |
| Per tool | Title, subtitle, tech tags, **three benefit cards**, a heading, then a demo carousel | The cards answer "why does this matter" before the carousel answers "what does it look like". Max wrote all nine card texts. |
| Shared, below the sub-tabs | The component table only | It describes hub-wide infrastructure rather than one tool |

The page is deliberately near-prose-free. Earlier drafts had paragraph intros on every tab and an
eight-card life-cycle carousel with no image at all; Max cut all of it on 2026-09-09. Bullets and
the demo carousels only. Do not reintroduce explanatory paragraphs.

### Verified (after the merge, headless; superseded 2026-09-10)

This describes the screenshot version of the page. The carousels that replaced it were verified
separately; see their sections below.

Tabs and both sets of sub-tabs switch, and switching a Hub tool no longer disturbs Sprout's state;
both Hub carousels advance and report `01 / 02` and `01 / 03`; the arrows sit fully outside the
image with their centre exactly on the image centre (dy = 0); the canvas renders at ratio 1.600
with pin 3 landing at 57% / 30.9% against 57% / 31% authored; no broken images; zero script errors;
zero em dashes. `#tab-progress`, `#tab-workflow`, `#composition` and `composer-hub.html` all still
land on the Hub.

Note: the page used to make ~2100 requests with ~700 failures on load. **Fixed 2026-09-10**; see
"Loom embeds load on demand" under Current Portfolio State.

### Open items

1. ~~**The chaconne slide has no overlay callouts yet.**~~ **Superseded 2026-09-09.** Max scrapped
   the screenshot approach for the Compass panel entirely. The replacement is
   `demo/compass-demo.html`, built and verified the same day and transplanted 2026-09-10.
2. ~~**A Constitution / annotated-guide screenshot**~~ **Solved by the carousel.** Slides 3 and 4
   show the Constitution as live HTML, including a rule being amended. It never becomes a
   screenshot.
3. **`Software Developer Resume.pdf` is unlinked.** Decide whether the software track needs its
   own route (`resume-dev.html`) alongside the academic CV.
4. **"The composer stays the author" is unused.** It was the heading over the shared card block
   before the cards went per-tool. Strongest line on the page; natural home is above the Compass
   cards.
5. **Rebuild the Workflow tab** when there is something worth putting in it.

### Iteration on the Compass carousel, 2026-09-10 (live, pushed)

Max drove this pass line by line off Vercel preview deploys. The shape it settled into:

**The copy is Max's, not mine.** Each slide carries a large plain-language title in his words,
and the earlier engineer's phrasing ("compile into a single artifact", "MuseScore headless",
"standing context injected at a chokepoint") is gone from the visible page. Do not write it back.

| # | Title (large, per slide) | State of the piece |
|---|---|---|
| 1 | Teach your assistant about your musical aesthetics. | This information allows your assistant to make better observations and suggestions. |
| 2 | Discuss the goals and identity of your piece. | Initial idea: Bass fugue: five modules, one mega-subject. |
| 3 | Settle on your piece's constitution and receive feedback. | Decide what the piece is and what it isn't (this can always be edited). |
| 4 | Share musical ideas, refine your constitution, upload full drafts via XML for full musical analysis. | Refined and pivoted to a chaconne after discussion with assistant. |
| 5 | Let your assistant be your engraving guide. | *(none: a slide with an empty `state` hides the whole block, label included)* |

**Structural changes, in the order they happened:**

1. **Side arrows** float over the canvas edges, centred on the slide rather than the whole stage.
   They and the arrows under the stage are one control, driven from the same arrays.
2. **The caption strip moved above the slide** and became the slide's header. Watch out: it is a
   **column** flex container now, and flex-basis applies to height there, so the old
   `flex: 1 1 300px` on `.demo-cap-col` was forcing a 300px empty band. It is `flex: 0 0 auto`.
3. **The line under the rail is gone.** It was one static sentence repeated on every slide, which
   read as if every slide were the Blueprint slide. Its text became slide 1's title, and the
   per-slide titles took over that job.
4. **The Blueprint band is tight**: 10px above the tag, 12px below the graphic, 92px tall. The
   AMENDS label had to move **onto** the curve (with a `paint-order` halo knocking out the line
   behind it) so the graphic ends in the same place whether the label shows or not. Otherwise the
   panel cannot close up without the label falling out the bottom.
5. **The rail is boxed by slide, and the box is the control.** Each slide's nodes sit in one
   rounded box; clicking it goes to that slide. The pills inside are `<span>`s now, not buttons
   (a button inside a button is invalid). Keyboard reachable via `role="button"` + Enter/Space.

**Claims Max removed, and why they must not come back:**

- **The tool does not engrave.** The "engraves" arrow into the finished score is gone, and the
  checklist's button reads "Save checklist", not "Send to engraver". The score sits on slide 5 as
  the thing you document after engraving it yourself. (The rail still draws Engraving → Score as a
  plain chain arrow; Max was asked about it and has not called it, so leave it.)
- **The "contradicts" and "becomes" arrows on slide 4 are gone.** Three connector arrows survive
  and he has not objected to them: "compiles to" (slide 2), "binds" (slide 3), "returns" (slide 5).

~~**Still open:** the short step name still sits at the bottom centre of the controls
("The Aesthetic Blueprint", "Constitution to Guide"), which is now a second title on the slide.~~
**Resolved 2026-09-13:** the whole controls row is hidden on the page; see "Strip navigation and
hover notes".

### The Compass demo carousel (built 2026-09-09, transplanted 2026-09-10)

**It is now the Compass panel.** The annotated-screenshot carousel it replaced is gone from
`index.html`; `images/Hub_Compass_Canvas.png` is unreferenced as a result, and
`images/Hub_Chaconne_Score.webp` is still used (the carousel reuses it for the draft and the
engraved page). The CRM and Agency panels became carousels the same day; see "The CRM and Agency
carousels" below.

`demo/compass-demo.html` **stays on disk as the iteration source.** Change slides there, look at
them in isolation, then re-transplant. The two copies were kept byte-identical in their shared
CSS and markup through the layout tuning below; keep doing that.

**Why it exists.** The screenshot walkthrough failed for a structural reason: the app's UI text
renders around 4px at page width, so the numbered pills had to become the readable layer. The page
was showing the *container* and annotating it, because the *contents* were illegible. Max scrapped
the screenshots for the Compass panel and asked for a carousel that walks one piece from first
contact to finished score.

**The fix is the inversion.** Every slide is a faithful HTML rebuild of the real node UI, filled
with example content, at real reading size. No screenshots anywhere. Design tokens come from
`app-ui/src/styles/tokens.css` and node chrome from the node CSS modules, so it reads as the real
canvas: Cormorant Garamond and DM Sans, the warm cream palette, dark node headers with amber
uppercase type, grey inbound and amber outbound ports, faint manuscript staff rules on the canvas.
It also fixes the known mobile problem for free: live text reflows where a pinned image does not.

**The five slides.** Order set by Max.

| # | Slide | Shows |
|---|---|---|
| 1 | Aesthetic Blueprint | The overlay's real five fields: Voice, Influences, Tendencies, Parameters, Philosophy |
| 2 | Intake | Dialogue and Form modes side by side, compiling into the Intake artifact |
| 3 | Constitution to Guide | Four rules with a `Source:` citation, then the one-sheet the Guide emits |
| 4 | Sketches to final draft | The sketch that contradicts rule 1, the amendment, `History (3)`, the draft |
| 5 | Engraving assistant | House style in, engraving checklist out, then the engraved page and the recording |

**The narrative.** One piece: a bass fugue that becomes *Chaconne for Bass and Pedal Board*. The
turn happens on slide 4 and the real Constitution rules set it up. Rule 2 (the subject must be
sparse, because a groove-forward line saturates the delay buffer) and rule 4 (delay time equals
phrase length) both describe the pedal returning material on a fixed cycle, which is ostinato
behaviour. A mensuration canon fights that; a chaconne is native to it. **This causality is a
reconstruction from the rules on disk, not something written down in the Compass repo.** Max has
not confirmed or corrected it. If it is wrong, slide 4's dialogue and proposed decision are the
only text that changes.

**The chain rail.** A persistent strip above every slide, drawn from the real graph in
`app-ui/src/utils/compileContext.js` (its `HANDLE_ACCEPTS` map says which port takes what).
Upstream nodes are solid but dim, the active node is lit, downstream nodes are ghosted outlines.
It replaces dot navigation and is clickable.

Two things about it that must not be undone:

1. **The Blueprint is not a node in the rail.** `compileContext.js`: it is "standing context
   injected into every agent call at the single chokepoint". So it renders as the tinted field
   *behind* the whole rail, and slide 1 lights that field rather than a pill. Making it the first
   node would be both wrong and a weaker idea.
2. **The back edge is the point of the rail.** On slide 4 an arrow runs right to left from Sketch
   into Constitution, labeled AMENDS. It is the frame that proves the canvas is a loop rather than
   a pipeline. It is drawn as real SVG measured off the pill positions, and it lives on
   `.demo-rail-field`, **not** inside `.demo-rail`, because `.demo-rail` sets `overflow-x: auto`
   which forces `overflow-y` to auto and silently clips anything drawn below the pills. That cost
   a debugging round; do not move it back.

**Verified headless (Playwright, 2026-09-09).** Zero script errors, zero failed requests, no broken
images, zero em dashes, all five slides switch, rail states correct on each (field lit only on
slide 1, back edge amber only on slide 4, edges filling 0/1/3/4/6), no horizontal overflow at
1280px or 390px.

**Deliberate deviations from the app**, so a future session does not "correct" them:

- App labels use em dashes (`SECTION 1 — STRUCTURAL MODEL`). Rendered here with a middot, so the
  portfolio's zero-em-dash rule keeps holding.
- The Engraving node appears twice side by side, House style tab then Checklist tab. Same
  one-node-two-faces pattern slide 2 uses for Intake.
- Slide 4's draft is the real Chaconne page cropped and desaturated, so it does not read as the
  identical picture to slide 5's engraved page.

**The engraving slide is better grounded than it looks.** An engraving-assistant *node* does not
exist on the canvas, but everything it shows does: `mcp/musescore-engraver/engrave.py` (MuseScore 4
headless, inbox to outbox, real PDFs), `HOUSE_STYLE` in `app-ui/src/utils/notationSys.js` (the
Verovio profile matched to MuseScore's Leland so preview and PDF agree), and an engraver system
prompt surviving in an older Next build of Compass that names publisher house styles (Henle,
Bärenreiter, Universal, Boosey, Peters, Faber, Chester) and asks the agent to "help build a
publication-ready order of operations". That last phrase is the checklist, already specified.

**How the transplant was scoped**, since it lives on a dark Tailwind page now:

- Everything is under `.compass-demo`. The app's design tokens sit on **that element, not
  `:root`**, so they cannot reach the rest of the page. The light palette reads as one cream card
  on the dark page, the way the annotated screenshots used to.
- Tailwind's preflight strips list markers, so `.compass-demo .dbucket ul` puts `list-style: disc`
  back for the Guide one-sheet.
- Arrow keys are bound to the carousel, not to `document`, so they do not hijack page scrolling.
  It takes focus on mousedown (`tabindex="-1"`).
- `switchTab()` and `switchTool()` already dispatch a `resize`, which is the rail's redraw hook, so
  tabbing away and back re-measures the back edge. Verified.
- Cormorant Garamond and DM Sans were added to the existing Google Fonts link.

**The layout had to be tuned for the card, and the lesson generalizes:** the portfolio card gives
the carousel an **872px canvas**, not the 1180px the standalone page has. A wrapping flex line
breaks on **flex-basis clamped by min-width**, not on the preference, so the three-node slides kept
wrapping until both came down (`.dnode` and `.dpiece` are now basis-equals-floor, and they grow
from there). If a slide ever wraps to two rows again, that is the knob.

**Audio (done 2026-09-10).** Slide 5 used to hotlink the full 12MB, 12:39 `chaconne.mp3` from
composer-portfolio-nu.vercel.app. It now plays `demo/assets/chaconne-excerpt.mp3`: exactly 45
seconds from 8:25, the timestamp Max picked, 160 kbps and about 880 KB, with a 0.5s fade in and a
1.5s fade out so it does not start or stop mid-note. Cut with ffmpeg from
`composers-compass/portfolio/site/assets/audio/chaconne.mp3`, which is byte-identical to the
deployed copy, so 8:25 is the same moment the live composer site plays. `index.html` points at
`demo/assets/...` and the standalone at `assets/...`.

**The Blueprint tag is slide 1's control (2026-09-10).** Because the Blueprint is the field and
not a pill, nothing in the rail went back to slide 1. The "Aesthetic Blueprint · On" tag now does
it (click, Enter, Space). Its hit-area padding is cancelled by equal negative margins, measured at
0px of movement. A "Click through the process" hint sits opposite it on the same line.

The Compass panel's three benefit cards and the heading "A visualized creative process, not a chat
window" are untouched and still sit above it.

### The CRM and Agency carousels (built and transplanted 2026-09-10)

Same treatment as Compass, same workflow: built standalone in `demo/crm-demo.html` and
`demo/agency-demo.html`, settled with Max slide by slide, then transplanted over the annotated
screenshots. The standalones stay the iteration sources; keep them in sync with `index.html`.

**CRM, seven slides.** One fictional roster throughout (Priya Anand, Jordan Ma, Marcus Webb, Naomi
Cole, Desmond Okafor, Sofia Lindqvist, Theo Lindgren) and one concert, Groove Theory II on
Oct 18, 2026, which ties the slides together: Jordan is confirmed for it on Contacts, and the
October newsletter announces its premiere.

| # | Nav | Slide |
|---|---|---|
| 1 | Contacts | Contacts table behind the Edit contact modal |
| 2 | Outreach | Outreach queue behind the Email 1 reconnect draft (the app's real template, verbatim) |
| 3 | Concerts | Booking portal: essentials progress, private link, answers |
| 4 | Concerts | Checklist laid over an October calendar |
| 5 | Concerts | Lineup and RSVPs |
| 6 | Concerts | Communications log |
| 7 | Newsletter | Editor with a brain-dump, the Polish result, and the live preview |

The four Concerts slides share one dashboard background and each opens a different section's
popup. That structure was Max's, and the booking portal slide was his addition.

**Virtual Agency, two slides.** A Claude Code transcript creating the Music Marketing employee,
with the existing "Putting one to work" steps under it, then the real job description and
`sprint-01-groove-theory.md` as document cards, condensed from `../virtual-agency/`.

**Content calls to keep:**

- **Placeholder data only.** Max asked explicitly for the Concerts lineup to drop the real names
  his screenshot showed.
- **The sprint card omits that sprint's contact-research table.** It is scraped work emails for
  named people at outside institutions, which are not ours to republish.
- **The booking portal slide does not say the link is local-only** (Max's call, 2026-09-10, under
  the Accuracy stance below). The app's own note that the link only opens in this browser was
  removed, and the shown URL elides its host rather than reading `localhost`, which said the same
  thing. The note's first sentence stays, because it describes the feature rather than a gap:
  anyone with the link can read and edit the whole form, so treat it as the password.

**How three carousels share one page** (the part that needed care):

- All three use the same `demo-` scaffolding classes. The Compass script used document-wide
  queries, which would have counted the CRM and Agency slides as its own, so its queries are
  scoped to `#compassDemo`. Never add a document-wide `.demo-car-slide` query.
- CRM and Agency run off one shared initializer keyed on `[data-demo-panel]`, with no ids.
  Captions live on each slide (`data-title`, `data-contrib`, `data-state-label`, `data-state`),
  and each slide names its nav group with `data-nav`, so one nav entry can span a run of slides
  (Concerts is four) and a slide can be inserted mid-run without renumbering.
- One token block and card rule serve `.compass-demo, .crm-demo, .agency-demo`. CRM chrome is
  `c`-prefixed, lifted from `crm/components/crm.module.css`; Agency chrome is `a`-prefixed.
- The CRM and Agency nav strips carry a "Click any section" hint, the same job as the Compass
  rail's hint.

**Two fixes found in verification:** the contacts table is about 620px inside a clipping frame, so
on a phone its last columns were unreachable (now a scroll container), and the job description
card cut off mid-list (the document cards now fade at the bottom).

**Unreferenced now, left in place:** `initHubCarousels()` and the `.hub-car-*` CSS (no markup
left), the `.annot` / `.pin` / `.hub-shot` rules, and `images/Hub_CRM_*.png` plus
`images/Hub_Agency_Roster.png`.

### Pinned tool tabs (2026-09-10)

Both tool rows, Hub and Sprout, are `.tool-tabs`: sticky directly under the main tab bar, which is
itself sticky under the fixed nav. **The row is deliberately narrower than the full-width bar
above it.** Max likes that the two read as different levels of tab; do not make it full-bleed.

- `--tabbar-h` is **measured** in JS (`measureTabBar()`), because the tab bar changes height when
  it wraps, and the row's `top` sits on it.
- Every scroll-into-view subtracts one `stickyOffset()` (nav + tab bar + the visible tab's tool
  row). Use it for any new jump; do not hand-roll offsets.
- Below 640px the row is one swipeable line, left-aligned so an overflowing row never clips its
  first button out of reach. **Wrap and alignment live in `.tool-tabs`, not in `flex-wrap` /
  `justify-center` utilities:** the Tailwind Play CDN injects its styles after this page's, so an
  equal-specificity utility silently beat the media query. That cost a verification round.
- The row releases at the end of its tab panel on purpose, so it never hovers over the Contact
  section.
- **Clicking a tool tab scrolls to the top of that tool's card** (added 2026-09-10 at Max's ask),
  the same way a main tab lands on its panel: `switchTool(id)` scrolls so the card sits
  `stickyOffset() + 16` from the top. Hash navigation calls `switchTool(id, true)` to skip it,
  because it scrolls to the same card itself 100ms later and two smooth scrolls fight. Verified at
  1280 and 420 wide on both tabs, from deep inside a card and from the page top: the card lands at
  exactly 184px (57 nav, 57 tab bar, 54 row, 16 gap), and hash links still land at +24.

### Strip navigation and hover notes (2026-09-13, not pushed)

At Max's ask, on all eight carousels. Page only; the `demo/` standalones are unchanged.

- **No arrows.** The side arrows and the arrow row under each stage (with its step name and
  `01 / 05` count) are hidden in CSS. The markup stays so a re-transplant still lands clean. The
  strip, or the Compass rail, is the control. The arrow keys still work.
- **The "next" cue.** Whichever control leads to the following slide gets `is-next`: a dashed
  outline and a pulsing corner dot on strip entries (a dot, not an arrow glyph, so the strip never
  changes width), and a dashed glowing border on Compass rail groups. The last slide has no cue.
- **Step chips.** A strip entry that covers a run of slides gets numbered chips beside it while
  that run is showing (Hub CRM Concerts 1 to 4, TeacherAID Booking 1 and 2), built by the shared
  carousel script. Without them those slides were unreachable once the arrows went.
- Strip hints read "Click to step through" (Compass keeps "Click through the process"), tightened
  so the strips stay one line.
- **Hover notes.** On all eight carousels (Compass, CRM and Agency were added later the same
  day, see "Compass pins and notes" and "CRM and Agency pins") the numbered notes row is hidden
  (`.has-pop`, set by the script). Each note pops up beside its pin when the pin's parent element
  (its tile) is hovered, focused (tiles get `tabindex="0"`) or tapped; a tap elsewhere closes it.
  The tile gets an outline in the pin color and the pin scales up. The popover is
  `position: fixed`, anchored under the pin but never under the pinned strip and title card, and it
  follows scroll. **The `.demo-notes` markup is still the text source,** so notes are edited in the
  same place as before.
- The title card's "State of" label carries a "Hover a number for details" pill ("Tap a number" on
  touch) on slides that have pins.
- **Verified headless (1280, and 390 with touch):** all eight carousels walk every slide by
  clicking only the `is-next` control (Hub CRM 0 to 6 through the Concerts chips, TeacherAID 0 to
  5 through the Booking chips), with no cue on the last slide; arrows and controls computed hidden;
  arrow keys still step; every strip one line (50 to 56px, Compass rail 102px); all 75 numbered
  tiles show the right note on hover, inside the viewport and below the pinned layers, and hide on
  leave; keyboard focus shows and blur hides; a tap shows and a tap elsewhere hides; zero script
  errors, em dash count unchanged. Test note: the page's smooth scrolling moves targets under a
  parked cursor, so hover checks need `scroll-behavior: auto` and a wait after a slide jump.

### Compass pins and notes (2026-09-13, pushed)

At Max's ask, the Compass carousel gets numbered blurbs like the other carousels, in both copies.
On the page they are hover and tap popovers; the standalone shows them as a notes row.

**How it shipped:** a parallel session's commit `0b73ae2` staged `index.html` while this work sat in
the working tree, so the page's pins, notes and `initDemoPops()` went live inside that commit,
whose message does not mention them (`git log -S initDemoPops` points there). The two phone fixes
below, the standalone and these docs followed in their own commit.

- **13 pins, one per node** except slide 1: the Blueprint's two columns (Voice, Influences,
  Tendencies / Parameters, Philosophy); Intake Dialogue, Intake Form, the intake artifact;
  Constitution, Guide; Sketch, Constitution revising, the draft; House style, Checklist, the
  engraved score. One sentence each, Claude's draft; Max has not called them. They describe
  capability only, and the engraving notes do not claim the tool engraves.
- **Placement.** `.dnode` and `.dpiece` clip overflow (it keeps the ports half-sunk), so the default
  -10px corner pin was cut off. A whole-node pin sits inside the dark header (`top: 7px; left: 9px`,
  and the head gets `padding-left: 39px`), a picture's pin sits on the image corner, and the
  Blueprint column pins use `.dpin-tr`, top right over the empty end of the first label.
- **Shared popover code.** The popover and below-the-fold dock moved out of the `[data-demo-panel]`
  initializer into a global `initDemoPops(root, slides, getCurrent)` in the shared script, beside
  `alignUnderPin()`. It returns `hide()` and `updateDock()`; both the Compass script and the panel
  initializer call it from `show()`. Its "never under the pinned layers" floor now also counts
  `.demo-rail-field`.
- **Slide 5 has no state line,** so the "Hover a number" pill had nothing to hang on. Its caption
  column stays up with `.is-hint-only`: the label text drops to font-size 0 and only the pill shows.
- **Two phone fixes found on the way, both copies:**
  - The Blueprint columns had `min-width: 270px` inside a card about 226px wide on a phone, so the
    right side of both columns was already cut off. Now `min(270px, 100%)`.
  - Below 640px the rail is `position: relative` but kept its sticky `top` (`--demo-pin-top`, about
    187px), which a relative element reads as an offset. It sat over the title card and the top of
    every slide on a phone. Now `top: auto`.
- **Verified headless (1280, and 390 with touch):** 191 checks, 0 failures, zero script errors. Pin
  counts per slide, one note per pin, every pin has a tile and none is clipped, each popover shows
  the right note inside the viewport and below the pinned title card, the pill shows on all five
  slides (pill only on slide 5), dock chips match the pins below the fold, TeacherAID and Sprout CRM
  popovers still work through the shared function, and the standalone shows its notes row with
  unclipped pins. Screenshots checked by eye.

### CRM and Agency pins (2026-09-13, pushed)

At Max's ask, the rest of the Composer Hub gets numbered blurbs too, in `index.html`,
`demo/crm-demo.html` and `demo/agency-demo.html`. The page needed no script change: the
`[data-demo-panel]` initializer already runs `initDemoPops()`.

- **CRM, 18 pins:** Contacts 3 (the popup's tabs, Roles, the footer), Outreach 3 (popup header,
  Body, footer), booking portal 3 (header, private link box, answers), checklist 2 (header,
  calendar), lineup 2 (header, an inline pin beside Priya's RSVP), communications 2 (header, an
  inline pin beside the Replied tag), Newsletter 3 (the Sections, Send and Preview cards).
- **Agency, 4 pins:** the Claude Code chat card and the Putting one to work box; the job
  description and sprint cards.
- **Pins stay in the part of a popup you can see.** Popups scroll, so a pin further down a popup
  body sits below the visible part and cannot be hovered. The first pass put pins on the checklist
  lists, Naomi's RSVP, the Awaiting entry and the Relationship field, and all four were unreachable.
  They moved to the popup header, the footer, or the top rows. Check reachability, not just
  placement, before pinning anything inside `.cmbody`.
- **Placement classes** (CSS scoped to `.crm-demo` and `.agency-demo` on the page):
  `.cmhead.demo-pinned` insets its pin ahead of the title (`padding-left: 46px`); a `.cmfoot` pin
  sits on the footer's top edge at `left: 6px`, clear of the text above it; `.cpin-tr` puts a pin
  top right of a field, over the empty end of its label; `.cpin-inline` is an inline pin whose
  parent row is the tile; the chat card's pin sits in its dark title bar. Cards and the Agency
  document columns use the default hanging pin.
- Copy is Claude's draft; Max has not called it. Nothing on the booking portal slide says the link
  is local-only.
- **Verified headless (1280, and 390 with touch):** 271 checks, 0 failures, zero script errors.
  For every slide: pin count, one note per pin, every pin has a tile, no pin clipped by any
  scrolling or clipping ancestor, every pin reachable at its center, its popover shows the right
  note inside the viewport and below the pinned title card, and the hint pill shows. The standalones
  show their notes rows with unclipped pins. The Compass suite still passes 191 of 191.
  Screenshots checked by eye.

### Pinned title cards (2026-09-13, not pushed)

At Max's ask, every carousel's title card (`.demo-caption`: the big slide title and "State of"
line) pins too, for all slides.

- **Stack, top down:** strip (`--demo-pin-top`), title card (`+ --demo-strip-h`), then the Sprout
  suite's notes rows (`+ --demo-cap-h`). The notes rows are hidden since they became popovers (see
  "Strip navigation and hover notes"); the rule stays for the no-script fallback. TeacherAID is the exception: its strip sits under the
  title card, so the card pins at `--demo-pin-top` and the strip under it.
- `measureDemoPin(root)` publishes both heights per carousel. `measureTabBar()` calls it for
  every root, and both carousel scripts call it in `show()`, because titles wrap to different
  heights slide to slide.
- **Layering for the release** at the end of a carousel: strips z 27, title card 25, notes 24,
  all under the tool row (30), so each slides under the one above it.
- **The base `.demo-stage` is `overflow: clip` now** (with `hidden` as the fallback). `hidden`
  made the stage a scroll container, so the title card stuck to the stage instead of the page.
- **Below 640px the title card scrolls away**, like the notes rows, and TeacherAID's strip goes
  back to pinning at `--demo-pin-top`.
- Page only: the standalone demos in `demo/` do not pin their title cards.
- Verified headless at 1280 on all eight carousels, 150px into a pin: each layer sits exactly on
  the one above, the title card paints over the slide, a slide change while pinned lands with
  delta 0; at 390 every title card is static; zero script errors.

### Pinned carousel strips (2026-09-12, pushed)

The Compass rail and the CRM, Agency and TeacherAID nav strips are `position: sticky`, so they
stay in view while a tall slide scrolls under them and release at the end of their carousel.

- They pin at `--demo-pin-top`: `3.5rem + --tabbar-h + --toolrow-h`. `measureTabBar()` measures
  `--toolrow-h` from the visible tab's tool row (0 on TeacherAID). The standalone demos leave
  the variable unset, so their strips pin at 0.
- **Sticky dies under any ancestor with `overflow: hidden`.** The TeacherAID strip sits inside
  `.demo-stage`, so that stage uses `overflow: clip; display: flow-root` instead. Do not put
  `hidden` back.
- The rail's tint now has `var(--cream)` under it, because a translucent pinned rail showed the
  slide through.
- Slide changes go through `turn(i)`, not `show(i)`: `alignUnderPin()` scrolls the new slide's
  top back up under the strip when it is pinned, so you do not land partway into the next slide.
- **Below 640px** the nav strips become one swipeable line (they wrapped to 91 to 135px), and the
  102px Compass rail does not pin, because the page already pins about 190px of bars on a phone.
- Verified headless at 1280 and 390: each strip pins exactly at the tool row's bottom (167px
  Hub, 113px TeacherAID at 1280), sits above slide content, and a slide change from deep in a
  carousel lands with delta 0. All four standalones pin at 0. Zero script errors.

### The merge (done, 2026-09-09)

Folded into `index.html` as the **first tab**, replacing the old "Building" tab. The tabs went
from a status axis (Shipped / Building / Workflow) to a project axis (The Composer Hub /
Sprout Society Suite), which also stops the Hub being filed under "not finished".

It mirrors the Sprout tab exactly: suite banner, three `tool-btn` sub-tabs, one card per tool,
then the shared argument and component table. No nested tab row.

Four things a future session needs to know before touching it (1 and 2 are historical since
2026-09-10: no Hub panel uses screenshots, and `initHubCarousels()` finds no markup):

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

## The TeacherAID tab (added 2026-09-12)

The teaching studio app from `../dasha-board/`, shown on the page as **TeacherAID** (renamed from
Dasha-Board the same day as Teacherade, then renamed TeacherAID at Max's call on 2026-09-13, by way
of Teacher-ade; the internal ids `tab-dasha`, `.dasha-demo` and the demo filename keep the old name
on purpose, and the `#teacherade` id and hash keep the earlier spelling) as its own main tab between the Hub and
Sprout. Built standalone in `demo/dasha-demo.html`, settled with Max, then transplanted by
script. **That file stays the iteration source**; change slides there, then re-copy.

**Six slides, nav strip in the app's tab order:** Schedule (logging today), Hours (review and
submit), Students (roster and profile), Booking (teacher's side), Booking (family's side),
Business. Max cut the week, month, hours sheet, Add Student and Ask slides; **Ask stays out
until he reworks that feature in the app.**

**How it differs from the Hub carousels, on purpose:**

- **The nav strip sits inside the stage, below the title header** (Max's call), as a square band.
  Scoped as `.dasha-demo .demo-stage .demo-nav-wrap`, so the CRM and Agency strips are untouched.
- **Annotations.** Each slide has one-sentence numbered notes (`.demo-notes`) and a matching amber
  pin (`.demo-pin`) on the feature. One sentence per note, Max's rule. On the page the notes row is
  hidden and each note pops up on its tile (2026-09-13, "Strip navigation and hover notes"); the
  standalone still shows the row.
- **Schedule slide order (2026-09-13, Max's call):** the lesson carrying pin 1 and the log buttons,
  Mira Okonkwo, is the first block of the day at 8:00&ndash;9:00. The Booking slide still shows her
  regular lesson on Tuesdays at 6 PM; not reconciled yet.
- **No pronouns for the user.** Copy says "the teacher", never she/her, and never names Dasha,
  and the product is called TeacherAID on the page. Max wants it to read as applicable to any teacher.
- **Screens use the app's own look** (IBM Plex, Newsreader, cool grey), not the Hub's cream.
  Classes are `ds-` prefixed; tokens are `--ds-` prefixed and live on `.dasha-demo`.

**Placeholder data only:** 18 fictional students, fictional employers (Harbor Piano, Maple Music
School), fictional rates. Never the real ledger.

**Copy still owed by Max:** the three benefit cards, the banner bullets and the heading were
drafted by Claude at transplant time; the slide notes and captions were reviewed.

**Verified headless (2026-09-12, 1280 and 390):** three tabs in order, all three `[data-demo-panel]`
carousels initialize, the new tab switches and steps through six slides, its nav jumps, the CRM
carousel still advances independently, `#tab-dasha`, `#teacherade` and the old `#dasha-board` land on the tab, no pin is
clipped at desktop width, zero script errors, no new em dashes. At 390 the Hours pin 2 sits below
the dialog's own scroll, and the 36px page overflow is the pre-existing hero H1.

## The Sprout CRM carousel (transplanted 2026-09-12)

The Sprout CRM panel's Loom and its four-screenshot strip are gone. The panel is now the five-slide
carousel from `demo/sprout-crm-demo.html`, which a parallel session built (delivery note in
`sprout-crm-next/docs/deliveries/2026-09/2026-09-12/`). **That file stays the iteration source.**

- **Slides:** Dashboard, Contacts, Events Portal (tagged New), Newsletter, Outreach/Claude MCP.
  Placeholder data only; Sprout N Tell Vol. 4 is the one real name. The Problem / Solution /
  Outcome cards above it are unchanged.
- **Look:** Sprout's own palette and Lato (added to the Google Fonts link), a black nav strip with
  the wordmark, cyan active tab, fuchsia pins. Tokens live on `.sprout-demo`; app chrome is `sp-`.
- **Everything is scoped under `.sprout-demo`.** The standalone has unprefixed helpers (`.ph`,
  `.nl`, `.md-`, `.t-`, `.due-`), so the transplant prefixed every rule. Keep that on any
  re-transplant. `.sprout-demo` also joined the three shared selector lists (tokens, card rule,
  `--demo-pin-top`).
- **Two pinned layers.** The nav strip sits above the stage and pins like the CRM and Agency strips.
  The notes row pins directly under it at `--demo-pin-top + --demo-strip-h`; `measureTabBar()`
  measures the strip. Below 640px the notes scroll away.
- **Page-only deviations:** nav items use 11px side padding and the wordmark tighter spacing,
  because the card gives the strip about 875px and the hint wrapped at the standalone's spacing.
  The notes band margins match the page's canvas padding (26px, 14px under 760px).
- **Phone fix in both copies:** below 760px the contact detail panel stacks under the list instead
  of covering it (pin 1 used to float over the panel).

**Verified headless (2026-09-12, 1280, 1100, 1024 and 390):** five slides step and nav-jump, the
strip stays one line (51px), the notes pin exactly at the strip's bottom, a slide change while
pinned lands with delta 0, every pin sits inside the stage, no frame overflow, the Hub CRM carousel
still advances on its own, zero script errors, no new em dashes.

## The Grant, Social and Campaign carousels (transplanted 2026-09-12)

The last three Sprout panels, built the same way as the Sprout CRM carousel: one standalone per tool
in `demo/`, then copied into `index.html` by script. **The standalones stay the iteration sources.**
Each carries `TRANSPLANT CSS START / END` and `TRANSPLANT MARKUP START / END` markers; a
re-transplant copies what sits between them. Every selector between the CSS markers starts with the
root class, so nothing reaches the rest of the page.

| Panel | Root / prefix | Source app | Slides |
|---|---|---|---|
| Grant Finder | `.grant-demo` / `gf-` | `Grant Tool v2/components/GrantManagerV2.jsx` | Grant Pipeline, Import from Claude, Research Brief, Questions, Tasks, Export |
| Social Planner | `.social-demo` / `so-` | `sprout-social-tool/components/SocialManager.jsx` (V2) | Dashboard, Content Queue, Calendar, Create Post, Analytics |
| Campaign Tracker | `.campaign-demo` / `qt-` | `qr-tracker/public/index.html` | Dashboard, QR Codes, Daily Scans, Manage Events, Update Live |

- **Same behavior as the Sprout CRM carousel:** pinned nav strip, numbered notes pinned under it
  (`measureTabBar()` now measures the strip on all four Sprout roots), pins on the features. All three
  use the Sprout palette and Lato. **Campaign was first built in the real tracker's dark slate
  look, then repainted in the Sprout palette at Max's ask** so the suite reads as one set; its
  layout still follows the tracker. Do not "restore" the dark look. Its QR codes are decorative
  inline-SVG patterns (`qt-qr-a` to `qt-qr-d`) that encode nothing.
- **Placeholder world shared with the CRM carousel.** Sprout N Tell Vol. 4 on Sep 11, 2026 is the
  one real name. Funders, captions, the approver email, Instagram post IDs and scan counts are
  invented. Grant's ORG INFO answer says "Founded in Brooklyn in 2019", the one real org fact.
- **Grant shows Claude working in its own conversation,** from the research protocols, and the app
  taking the pasted grant profile JSON. That is how Grant Tool v2 works: it makes no Claude calls
  itself. Org-profile auto-fill is not shown; only the old V1 build has it.
- **Social is V2,** the live app: black and cyan, approval pipeline, publish to Instagram. The old
  `images/Social_*.png` screenshots were V1 (green, Brand Voice, AI captions). V2 has no Canva, AI
  caption or brand voice UI, so the slides show none.
- **Campaign's slides name no platform.** The live tracker runs on Vercel functions and Supabase,
  and the Cloudflare Worker is retired. The panel's tags and Solution card say Vercel (fixed
  2026-09-12); the slides leave hosting to them.
- `images/Grant_*.png`, `Social_*.png` and `QR_*.png` are unreferenced now, left on disk. The Grant
  and Campaign Looms are gone from the page, so `index.html` has no iframes left.
- **Page-only deviation:** Social's nav items use 10px side padding (both copies), because at the
  standalone's 14px the hint wrapped to a second line in the ~875px card.

**Verified headless (2026-09-12, 1280, 1024 and 390):** seven `[data-demo-panel]` carousels
initialize; Grant (6), Social (5) and Campaign (5) step by arrows and nav-jump with the right nav
item lit; every strip is one line (50 to 53px) and pins at the tool row's bottom (167px); the notes
row pins exactly at the strip's bottom; a slide change while pinned lands with delta 0; no element
wider than its stage outside a scroll container; the Sprout CRM carousel does not move when another
does; `#grant`, `#social` and `#qr` land on their panels; zero script errors, zero failed requests,
em dash count unchanged. At 390, Grant slide 1's pins 2 to 4 and Campaign slide 3's pin 3 sit inside
horizontal scrollers (reachable by swiping); the 36px page overflow is the pre-existing hero H1.

## Status Tags

```
.status-live    green    — deployed and actively used in production
.status-mvp     yellow   — functional but not in active production use
.status-wip     purple   — actively being built
```

---

## Current Portfolio State (September 2026)

This site is served from its Vercel default domain (ai-portfolio-landing-page.vercel.app). No custom domain is attached to it.

### Session of 2026-09-13: title cards, strip navigation, hover notes, Sprout notes, TeacherAID (pushed as `47e1acf`)

**Pushed to `main` in one commit at Max's call, without a fresh preview.** Max noticed the live page
was not updating: nothing from this session had been committed, and Vercel only deploys on push.
The commit carries `index.html`, `CLAUDE.md`, `demo/dasha-demo.html` and the four Sprout
standalones (`sprout-crm-demo`, `grant-demo`, `social-demo`, `campaign-demo`). The last preview,
`9oipv8abc`, predates the TeacherAID rename, so the live site is the first place the rename shows.

- **Sprout tech tags and cards fixed** at Max's call: Grant Finder reads Claude, Research
  Protocols, Next.js, Supabase, JSON; Social Planner lost the Canva API tag and its Solution card
  now reads "Direct Instagram publishing via API, with a human approval step before anything
  posts."; Campaign Tracker's tag and Solution card say Vercel instead of Cloudflare Workers. Do not
  put the old claims back.
- **Pinned title cards** on all eight carousels, under the strip (TeacherAID: above it). Details in
  "Pinned title cards".
- **Strip navigation and hover notes** on all eight carousels: arrows hidden, a "next" cue on the
  strip, step chips for multi-slide entries, and the numbered notes as popovers on their tiles.
  Details in "Strip navigation and hover notes".
- **TeacherAID Schedule slide:** Mira Okonkwo's lesson, the one carrying pin 1 and the log
  buttons, is now the first block of the day at 8:00&ndash;9:00 (was 6:00&ndash;7:00), in both
  copies.
- **Sprout notes are full sentences now** (Max's ask): all 57 short title-style notes on the four
  Sprout carousels (CRM 13, Grant 16, Social 16, Campaign 12) became one explanatory sentence
  each, TeacherAID length, in both the page and the standalones. Claude wrote them; Max has not
  called them. Grant's Import from Claude and Campaign's Update Live had explain boxes
  at the push; both became pinned notes afterwards (see below), so no Sprout carousel has one now. Verified headless at 1280 and 390: every Sprout popover shows the right sentence,
  inside the viewport and below the pinned layers, zero script errors.
- **Sprout CRM pin targets reshaped** at Max's call, both copies. A pin's tile is its parent
  element, so these use plain `demo-pinned` wrapper divs:
  - Contacts: pin 1 left the list tabs and now wraps the detail panel's profile block (tags,
    bucket, how they heard, affiliations); pin 2 wraps Next Actions and Touchpoints. Both notes
    rewritten to match.
  - Events Portal: pin 5 wraps the Links and Media tiles in one `sp-span2 sp-evd-grid` wrapper,
    so the pair keeps its two columns (one under 760px). Note 5 names both.
  - Newsletter: pin 2 wraps the reorder label and all five section blocks.
  - Outreach/Claude MCP: the "How Claude helps with outreach" box is gone; its content became
    four pinned notes: 1 the header (Outreach Manager, protocol, MCP, finds), 2 the tabs (new,
    grounded in `CRMManager.jsx` OutreachView), 3 the tier table, 4 the draft and rewrite box.
    Pins 3 and 4 sit top-right, because top-left covered the first letters of their headings.
    The `.sp-explain` CSS is now unused, left in place.
  - Verified headless at 1280 and 390: 63 Sprout popovers (was 59) all show the right note; each
    wrapper holds what it should (Links and Media side by side at 1280, stacked at 390; five
    section blocks under Newsletter pin 2); no pin clipped by an overflow ancestor; `#tool-crm`
    still has 5 slides with no tool panel nested inside it; the standalone loads clean; zero script
    errors. Screenshots checked by eye.
- **Renamed Teacherade to TeacherAID** at Max's call (briefly Teacher-ade first), in `index.html`
  (tab button, banner label, card title, comments), `demo/dasha-demo.html` (page title, heading)
  and this file. The `#teacherade` id and hash keep the old spelling so existing links still land.
  Not re-verified headless; text only.

All of it is verified headless unless noted; details sit in each section.

**After the first push (committed and pushed to `main` at the end of the session; see `git log`),**
Max drove more pin changes off the live site: Grant
Finder, Social Planner, Campaign Tracker and TeacherAID. `index.html`, `demo/grant-demo.html`,
`demo/social-demo.html`, `demo/campaign-demo.html` and `demo/dasha-demo.html` are modified.
**Preview:** https://ai-portfolio-landing-page-5tmx20gsx-mhperkins-projects.vercel.app (Vercel
login; no `--prod`). Production matches it after the end-of-session push.

- **Pipeline pins 2 to 4 outline their whole column** (Deadline, Progress, Next Action), header
  through the last grant. A column spans rows, so no element could be the tile. Each pin now
  carries `data-pin-for="gf-c-..."` and names a transparent `.demo-col[data-col]` overlay at the
  end of `.gf-pipe` (now `position: relative`). The shared page script takes that overlay as the
  target and sizes it to its header cell in `sizeCols()`, called from `show()`, on resize (tab
  and tool switches dispatch one) and on `document.fonts.ready`. The overlays sit after the rows
  so they paint above the header pins and catch hover anywhere in the column. The standalone has
  no popovers, so its overlays stay zero width. **Any future column note can reuse this.**
- **Import from Claude:** the "How Claude helps with grants" box is gone; its content became four
  pinned notes: 1 the how-to box (finds, protocols, verification), 2 the JSON zone (builds the
  profile), 3 the preview (funder research: tax filings, reviewer words, go or no-go), 4 the
  Import button. Pins 1 and 2 sit top-right so they do not cover text. `.gf-explain` CSS is now
  unused, left in place.
- **Portal link highlighted** at Max's ask (submitting is one click away once the answers are
  copied). It began as its own pin on the link and now lives in Export pin 1, the whole header
  card; see "Grant whole-card pins" below. `.gf-pin-after` CSS is unused, left in place.
- Verified headless at 1280 and 390: each column overlay matches its header cell and holds all 7
  cells of its column; hovering a Progress body cell shows note 3; the Import pins land on the
  right elements; no pin clipped; the standalone loads clean; zero script errors.
- **Social Content Queue:** pin 2 outlines the whole Vol. 4 lineup card and explains the path from
  the app to Instagram (drafted, approved with the approver's address stamped on, scheduled,
  published from the card). Pin 3 is on Save the Date's "Publish to Instagram" button and
  explains the publish call. It spent one round on a wrapper around the "Working..." button; Max
  said that looked wrong and wanted the Publish blurb back, so **do not pin "Working..." again.**
  Both notes are grounded in `sprout-social-tool`: `handleAdvance` in
  `components/SocialManager.jsx` and `app/api/instagram/route.js` (caption, hashtags and media URL
  go to Instagram through Composio; the route waits for the media container to finish
  processing, publishes, and the app saves the Instagram post ID). The approver email lost its
  own pin.
- **Social Create Post:** the right column (media type, schedule time, media link, flyer preview)
  is one tile, pin 2, about the post data, noting Instagram pulls the graphic from that link.
  Create Draft became pin 3; the old media-tab and schedule pins are gone.
- **Campaign Daily Scans:** pin 1 outlines the whole display through a `demo-pinned` wrapper around
  `.qt-frame` (the frame clips, so a pin inside it would be cut off). The range-button pin and the
  Aug 30 bar pin are gone; note 1 absorbs the flyer story.
- **Campaign Manage Events:** the code ID pin is gone; note 2 covers the whole add-code form,
  auto ID included.
- **Campaign Update Live:** the "How a scan works" box is gone. One pin on the whole Street
  Flyer code tile, with one note covering scan and count, Update Live, and Move. (Two pins
  nested inside that tile came first; Max said pins should not nest, one tile, one note.)
  The Street Flyer tile is now first in the Vol. 4 code list (Max's call), and a pinned
  `.qt-code` gets 16px top padding so its pin clears the label; the pin cannot sit further out
  because `.qt-evrow` clips and leaves only 10px beside a tile on phones. `.qt-explain`
  CSS is now unused, left in place.
- **TeacherAID Schedule:** pin 1 outlines the whole Mira Okonkwo lesson block instead of the log
  button row, sitting inside the block's top-right corner.
- Verified headless at 1280 and 390: each target holds what it should, no pin clipped, every
  popover shows, each standalone's pins match its notes, zero script errors. Screenshots checked
  by eye.
- **Grant whole-card pins, one blurb each** (Max's rule for this pass: a tile is the whole card,
  and its blurb lists the card's features):
  - Research Brief: pin 2 is the whole Funder Research Brief card (profile, fit and verdict,
    past grantees, voice, how it is scored, the program officer question). The FIT ANALYSIS and
    VOICE inline pins are gone; Framing Notes pin 1 stays.
  - Questions, top to bottom: 1 the tracker; 2 the whole ORG INFO card (added at Max's ask: the
    standard org details go into any grant, kept consistent with the org profile; it does not
    claim auto-fill, which only the old V1 build had); 3 the whole Narrative card (prompt and
    hint, character count, Edit and delete, History, Paste); 4 the whole Impact card, whose
    highlighted bracketed text is the gaps feature (Max's call: the gaps live in the text, not
    the footer badge). The old character-count, History/Paste and gap-badge pins are gone.
  - Tasks: pin 1 is the whole Tasks & Next Steps card; the three inline pins are gone.
  - Export: pin 1 is the grant header card (name, funder, status, ask, deadline, portal link),
    pin 2 the Export Answers card (layout and Copy All). The portal-link pin, the export-block pin
    and the Copy All pin are gone, so `.gf-pin-after` is unused now.
  - Whole-card pins use `.gf-pin-corner` (-13px, not the default -10px), because at 390 the
    default landed on the card titles, where the header padding drops to 12px.
- **Verified after the last change of the day** (headless, 1280 and 390): all 61 Sprout popovers
  show the right note; every whole-card pin clears its card title or label and is not clipped;
  Questions reads 1 to 4 top to bottom with the ORG INFO and Impact cards as tiles; Social pin 3
  is the Publish button and nothing wraps "Working..."; Update Live has one pin on the Street
  Flyer tile, first in the list; each standalone's pins match its notes; zero script errors.
- **Below-the-fold dock** (page only, shared script): while a carousel is on screen, every pin
  on the showing slide that sits below the visible screen gets a numbered chip in `.demo-dock`,
  a "More below" bar fixed at the bottom center. A chip scrolls its tile's top under the pinned
  strip and title card and opens its note. Details that cost a round each:
  - It measures and places against `visualViewport`, not `innerHeight`. With the page's 36px
    sideways overflow, a phone's layout viewport is taller than the screen and a plain
    `bottom: 16px` dock sat below the glass.
  - `dockHold` keeps the opened note through the scroll the chip starts (tiles slide under a
    still mouse and fire hover-out) until the mouse really moves more than 6px.
  - The chip's click stops propagation, or the carousel's tap handler closes the note at once.
  - Verified headless at 1280, 390, and 390 in Chrome mobile emulation: no dock at the page top;
    chips match exactly the pins below the fold; nothing covers a chip; a chip click or tap keeps
    its note open with the pin on screen and drops that chip; the dock hides at the carousel's
    end and follows Grant's pins after a tool switch; all 61 Sprout popovers still pass; zero
    script errors.

**Open:**
- TeacherAID's Booking slide still shows Mira's regular lesson on Tuesdays at 6 PM, which no longer
  matches the Schedule slide. Max was asked whether to move it and has not called it.
- The `demo/` standalones do not have the pinned title cards, hidden arrows, next cue or hover
  notes; those are page only. A re-transplant keeps working because the page rules sit outside the
  transplant markers.
- Max still owes the copy for the TeacherAID tab's three benefit cards, banner bullets and heading.
- Slide titles and notes on the Grant, Social and Campaign carousels are Claude's drafts; Max has
  not called them.
- Max has been clicking through and reshaping pins, but has not signed off on the copy of: the
  Sprout sentence notes, Contacts notes 1 and 2, the four Outreach notes (the tabs note is new
  copy), the four Import notes, Social Queue notes 2 and 3 and Create Post note 2, Campaign Daily
  Scans 1, Manage Events 2 and the single Update Live note, or the Grant whole-card notes
  (Research Brief 2, Questions 2 to 4, Tasks 1, Export 1 and 2).
- Max has not reviewed the 13 Compass notes, the 18 CRM notes or the 4 Agency notes (see "Compass
  pins and notes" and "CRM and Agency pins").

**Next:** Max clicks through the live site and calls the open copy items above. Pushed at the
end of the session with `index.html`, `CLAUDE.md` and the four changed standalones
(`grant-demo`, `social-demo`, `campaign-demo`, `dasha-demo`). Max had to ask why the live site
looked old; the cause was a session ending without a push, which the end-of-session protocol under
Deployment now prevents.

### Session of 2026-09-12: Teacherade (now TeacherAID) tab, pinned strips, all four Sprout carousels (pushed as `dee52ff`)

**Pushed to `main` in one commit,** and Vercel deploys on push. `index.html` carried every item
below interleaved, so the day could not be split into separate commits. The commit adds
`demo/dasha-demo.html`, `demo/grant-demo.html`, `demo/social-demo.html` and
`demo/campaign-demo.html`, and updates `index.html`, `CLAUDE.md` and the other four standalones.

- **Teacherade tab** (TeacherAID since 2026-09-13) added between the Hub and Sprout: six annotated slides from
  `demo/dasha-demo.html`. Details in "The TeacherAID tab".
- **Pinned carousel strips.** The Compass rail and the CRM, Agency and TeacherAID nav strips
  stay in view while a slide scrolls under them. Details in "Pinned carousel strips".
- **Sprout CRM carousel** replaces the Loom and the four screenshots on the Sprout CRM panel: five
  annotated slides from `demo/sprout-crm-demo.html`, which a parallel session built and committed.
  This session transplanted it and added one phone fix to both copies. Details in "The Sprout CRM
  carousel". `images/CRM_*.png` are now unreferenced, left on disk.
- **Grant, Social and Campaign carousels** replace the last Looms and screenshots on the Sprout
  tab: 6, 5 and 5 annotated slides from `demo/grant-demo.html`, `demo/social-demo.html` and
  `demo/campaign-demo.html` (all three untracked). Details in "The Grant, Social and Campaign
  carousels".
- **Fixed a nesting bug from the Sprout CRM transplant.** It dropped the `</div>` that closes
  `#tool-crm`, so the Grant, Social and Campaign panels sat inside the CRM panel and rendered blank
  whenever another Sprout tool was picked. The close is back (`<!-- /#tool-crm -->`).

All of it is verified headless. **Max asked for the push without a preview deploy,** so the live
site is the first place he clicks through it.

Max clicked through the live site after the push and confirmed it works. Open items and next steps
moved to the 2026-09-13 session above.

### Session of 2026-09-10: CRM and Agency carousels, pinned tabs (pushed)

Everything is pushed to `main`, and Vercel deploys on push.

- `155aff6`: the CRM (7 slides) and Agency (2 slides) carousels replace the last annotated
  screenshots, the Compass script is scoped to its own panel, and the Compass rail gets its "Click
  through the process" hint. Details in "The CRM and Agency carousels" above.
- `f81c79a`: tool rows pinned under the main tabs on both tabs, `stickyOffset()`, the phone
  single-line row, and "Click any section" hints. **This commit also carries a parallel session's
  Loom fix** (`syncVideos()` and `data-src` iframes). That change was uncommitted in the working
  tree when this commit staged with `git add -A`, so it shipped under a message that does not
  mention it; `git log -S syncVideos` points here. **Stage named files, never `-A`,** while another
  session might be working in this repo.
- `b662c9e`: the Blueprint tag returns the Compass rail to slide 1. The rail had no control for it,
  so after clicking Intake the arrows were the only way back.
- `6d3c174`: slide 5 plays a 45-second excerpt from 8:25
  (`demo/assets/chaconne-excerpt.mp3`) instead of hotlinking the full 12MB recording, and clicking a
  tool tab scrolls to the top of that tool's card. Both verified headless: the excerpt loads at
  45.0s in both copies, and tool switches land at exactly 184px on both tabs at both widths.

Verified headless throughout: each carousel counts only its own slides and none moves another; the
tool rows pin at exactly the tab bar's bottom (113px) at 1280 and 420 wide; zero script errors.
Loom was not re-tested on its own, but every tab and tool switch in these runs went through
`syncVideos()` without an error.

- `dad8ac2`: the booking portal slide drops the app's local-only note, at Max's call; see "The CRM
  and Agency carousels".

Nothing from this session is open. Matching docs in composers-compass: `55d49c6` and `8bdfa8c`.

### Session of 2026-09-09, later: the Compass demo carousel (pushed 2026-09-10 as `f3fc9fa`)

Max scrapped the screenshot walkthrough for the Compass panel and asked for a carousel instead:
slides that demo each step to a finished piece, built **separately from the portfolio** so the
slides could be settled without touching `index.html`. Brainstormed first at his instruction, then
built.

Result: `demo/compass-demo.html`, self-contained, unlinked, headless-verified. Five slides, each a
faithful HTML rebuild of a real node rather than a screenshot, with a persistent chain rail drawn
from the app's actual port map. Full detail, including the two structural decisions not to undo,
is in "The Compass demo carousel" above.

**Transplanted into `index.html` on 2026-09-10**, replacing the screenshot carousel on the Compass
panel. Verified headless after the merge: five slides switch, rail states correct on each, the
back edge redraws after a tab round-trip, the Sprout tab is unaffected, the remaining CRM/Agency
hub carousel still initializes, zero em dashes, zero script errors. The 426px-at-390px horizontal
overflow is the pre-existing hero H1, unchanged and unrelated.

Pushed as `f3fc9fa`. Before that it was reviewed on Vercel preview deploys (`vercel deploy`, no `--prod`); the folder is
now linked to the project, and `.vercel/` was added to `.gitignore` by the CLI. Preview URLs need a
Vercel login because deployment protection is on for previews.

**Then Max rewrote the whole panel's copy and reshaped it, 2026-09-10.** Large per-slide titles in
his own plain language, the repeated line under the rail removed, the band tightened, the rail
boxed by slide and clickable, side arrows added, and every claim that the tool engraves for you
taken out. Details and the exact copy are in "Iteration on the carousel, 2026-09-10" above.

### Session of 2026-09-09 (large restructure, pushed as `95aebfc`)

Everything below was live-verified headless and is now committed and pushed. The one later addition
in this block, the Loom fix, shipped inside `f81c79a` (see the 2026-09-10 session).

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

**Screenshots (historical: replaced by carousels on 2026-09-10).** All Hub screenshots carried numbered pills that name what they point at. The app's
own UI text renders around 4px at page width, so the pills are the readable layer, not a duplicate.
Two CRM screens were re-captured on 2026-09-09 because the originals showed empty states: the
Groove Theory II concert page and the newsletter editor. Seeding procedure and shapes are in the
Compass repo at `docs/deliveries/2026-09-09/README.md`.

**The CV replaced the resume.** `resume.html` is now the academic CV as a native page with a print
stylesheet, not a PDF iframe. Nav reads "CV" everywhere. `Software Developer Resume.pdf` is on disk
but **unlinked** — decide whether the software track needs its own route.

**Loom embeds load on demand (fixed 2026-09-10; pushed inside `f81c79a`).** Production was showing the Grant
Finder video as an empty box. Each Loom player pulls ~680 script files; all three Sprout players
mounted at once (hidden ones included) and `switchTab()` reloaded every iframe, so Chrome dropped
~800 requests with `ERR_INSUFFICIENT_RESOURCES` and whichever player lost its scripts rendered
blank. The video and markup were fine. Now each Loom iframe carries `data-src`, and
`syncVideos()` (called on load, in `switchTab()` and in `switchTool()`) gives a `src` only to the
visible one and strips it from hidden ones, which also stops playback on switch. Any new video
embed must use `data-src`, not `src`, or it reintroduces the problem. Verified headless: zero Loom
requests on load, one player at a time, all three render, `#grant` deep link works, zero resource
failures, zero script errors. A parallel session wrote this fix; it went out inside the tab-pinning
commit `f81c79a`, whose message does not mention it.

**Known, checked, and deliberately left alone** (both pre-existing, identical in the pre-merge
backup, neither caused by this work):
- Horizontal overflow at 390px, caused by the hero `H1` reaching 426px.
- ~~Pin labels scale with the image and render ~3.4px on a phone.~~ Moot since 2026-09-10: no Hub
  panel has pins any more.

**Remaining on the site itself:**
- ~~Loom for Social Media Manager V2 needs to be recorded~~ Moot since 2026-09-12: the Social
  Planner panel is a carousel.
- ~~The chaconne score slide has no overlay callouts yet.~~ Superseded: the screenshot carousel it
  belonged to is gone.
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

**Update, Sept 10, 2026:** the first ops-track application is ready. Wisconsin Chamber Orchestra,
Community Engagement & Education Associate, on the arts-education sub-track
(`career-search-arts-education-track.md`). Resume (one page, academic CV format, no AI wording),
final cover letter, and three application answers are done. **Not yet submitted;** priority
deadline is Sept 11. Remaining steps are in that file's Current State section.

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
