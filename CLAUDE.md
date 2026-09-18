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
| teaching.html (**branch `teaching-page` only, not on main**) | **Teaching page**, "Music and AI Integration" (built 2026-09-15): four topics as annotated carousels on the index.html carousel system, for the UW-Madison RISE-AI committee and the final-round live class. Kept off the live site until Max finalizes it; lives in the worktree folder `AI Tool Portfolio - teaching-page`. See "Session of 2026-09-15: the Teaching page" under Current Portfolio State. |
| [docs/wireframes/](docs/wireframes/) | Wireframes, per the global Wireframe Protocol. `2026-09-15_teaching-page.html` is the teaching page's (round 2). |
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
| [images/](images/) | Screenshots and assets. `maxwell-portrait-500/800.webp` is the color on-stage portrait from the composer portfolio's About section (copied 2026-09-14 from `composers-compass/portfolio/site/assets/portfolio/maxwell-about-portrait-*`), shown beside the About text on `about.html` and the home page. Not the black and white piano hero photo. |
| [career/](career/README.md) | **Everything for the job search** (moved here 2026-09-16): `tracks/` (the five career-search docs), `base/` (AI roles CV and base letter, ops resume), `applications/<YYYY-MM-org>/` (one folder per application: `job.md` with the posting link and a short job summary, `resume.md`, `letter.md`, `notes.md`, built `.docx` and `.pdf`), and `build.py`, which builds them all. **Start at `career/README.md`**: the application index, the source format and the build rules. `.gitignore` keeps it out of git (OneDrive is its only backup) and `.vercelignore` keeps it off the site. |

---

## Coding Conventions

- **No build tooling.** Do not add npm, webpack, Vite, or any build step. Everything runs directly in the browser.
- **Tailwind via CDN.** The `tailwind.config` script block at the top of each file extends the default theme. Do not install Tailwind as a package.
- **Custom CSS lives in `<style>` tags** in the `<head>` of each file. Use Tailwind utility classes for layout and spacing; use the `<style>` block for animations, custom component classes (`.card-hover`, `.tag`, `.status-live`, etc.), and anything Tailwind can't express cleanly.
- **No JavaScript frameworks.** Vanilla JS only, inline in `<script>` tags at the bottom of the body.
- **One file per page.** index.html, about.html, and resume.html are self-contained. Do not split into partials or components.
- **No em dashes.** Use commas, periods, or restructure the sentence.
- **Links out of a document open in a new tab (Max's rule, 2026-09-17).** On `resume.html` every body link
  carries `target="_blank" rel="noopener"`, including the walkthrough links into `index.html`. Site nav
  links stay same-tab.

---

## Deployment

**End-of-session protocol (Max's rule): update Current State, then commit and push to `main`
without waiting to be asked.** Vercel only builds production on a push, so a session that ends
on preview deploys leaves the live site behind. Stage named files, never `-A`.

Push to main. Vercel picks it up automatically. No build command, no output directory to configure — Vercel serves the files directly.

**Vercel serves every file in the repo except what `.vercelignore` lists** (`career/`, `docs/`,
`.claude/`, every `.md` and `.py`). Until 2026-09-16 there was no such file, and the career docs,
cover letters and application PDFs were all public at the site URL. A new non-site file type needs
a line there.

To test locally: open `index.html` in a browser, or run `npx serve .` if you need a local server for relative path testing.

---

## Portfolio Structure (index.html)

The page has tabbed sections. The sticky tab nav sits outside the hero section so it persists through the full page scroll.

| Tab | id | Content |
|---|---|---|
| The Composer Hub | `tab-hub` | Composer Compass, Composer CRM, Virtual Agency as three sub-tabs, then the component table. Default tab. |
| TeacherAID | `tab-dasha` | One tool, no sub-tabs: one card (tags, heading, the annotated carousel, then three benefit cards). Added 2026-09-12. |
| Sprout Society Suite | `tab-sprout` | CRM, Grant Assistant, Social Manager, Campaign Tracker as four sub-tabs. All four panels are annotated carousels as of 2026-09-12; no Sprout panel uses a Loom or screenshots now. |

Tabs are named for their **subject, not their status**. "Shipped / Building" was the old axis and
it filed the Hub under unfinished. Do not go back to it. Workflow was removed on 2026-09-09 and
will be rebuilt later; `#tab-workflow` and `#tab-progress` both resolve to `tab-hub` meanwhile.

Each project card has: a heading (Hub, TeacherAID) or a status badge (Sprout), a carousel, then three cards. No title, tagline or tech tag row since 2026-09-14.

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
| ~~Suite banner~~ | **Removed from all three tabs 2026-09-13** at Max's call: each tab opens straight on its tool row (TeacherAID on its card). Do not bring banners back. | |
| Sub-tabs | Compass / CRM / Agency | Three parallel tools, which is what tabs are for |
| Per tool | A large heading, a demo carousel, then **three benefit cards** (tech tags, title and subtitle removed 2026-09-14; the tool tabs name the tool) | Since 2026-09-13 (Max's call) the carousel comes first and the cards sit under it, on all eight tools, Sprout's Problem / Solution / Outcome cards included. Max wrote all nine Hub card texts. |
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
it (click, Enter, Space). Since 2026-09-14 it is boxed like the rail groups (Max's call: bare text
did not read as clickable), with their hover and, on slide 1, their active ring; the band's top
padding grew from 32px to 46px to hold the 32px box, 8px above the Intake group. A "Click through the process" hint sits under the Intake group (moved there from opposite the tag on
2026-09-14, Max's call; the band's bottom padding grew from 21px to 38px to hold it, back to 21px
below 660px where the hint hides).

The heading "A visualized creative process, not a chat window" sits above it; the Compass panel's
three benefit cards sit below it (moved there 2026-09-13).

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
- **The "next" cue.** Whichever control leads to the following slide gets `is-next`: a solid
  outline and a pulsing corner dot on strip entries (a dot, not an arrow glyph, so the strip never
  changes width), and a solid glowing border on Compass rail groups. (All dashed lines in the
  carousels became solid on 2026-09-14 at Max's call; do not bring dashes back.) The last slide has no cue.
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
  `position: fixed`, anchored **above** the pin since 2026-09-15 (see "Notes open above their pin"),
  and it follows scroll. **The `.demo-notes` markup is still the text source,** so notes are edited
  in the same place as before. Since 2026-09-16 each note is a bullet list (`ul.demo-bul`), not a
  sentence; see that day's session.
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

- **CRM, 18 pins:** Contacts 3 (the popup's tabs; the form from name to Prospect as one tile;
  Ensembles and Concerts as one tile about assigning them), Outreach 3 (popup header, Body,
  footer), booking portal 3 (header, private link box, answers), checklist 2 (header, calendar),
  lineup 2 (header, an inline pin beside Priya's RSVP), communications 2 (header, all six entries
  as one tile), Newsletter 3 (the Sections, Send and Preview cards).
- **One tile, one blurb (Max's call, applied twice here):** a run of related fields or rows is
  one tile whose blurb lists what it holds, not a pin per field. The contact form and the
  communications entries were reshaped this way. Wrappers are plain `demo-pinned` divs; inside a
  popup body, `.cmbody > .demo-pinned:not(:last-child)` restores the 11px field gap the wrapper
  swallows.
- **Agency, 4 pins:** the Claude Code chat card and the Putting one to work box; the job
  description and sprint cards.
- **Popups show whole (Max's call).** A popup used to sit `position: absolute` over the page
  behind it, so that page capped its height and the popup scrolled inside itself; on Outreach only
  the header and a sliver of the draft showed. Now `.cframe` is a one-cell grid holding both
  `.cpage` and `.coverlay`, `.coverlay` is `position: relative` and `.cmodal` has no max-height, so
  the frame grows to whichever is taller and the popup stays centered over the page. Both copies.
  The Outreach draft's textarea is 16 rows, enough for the whole template at desktop width.
  Before this, pins further down a popup were unreachable, which is why several CRM pins sit on
  popup headers; always check reachability, not just placement.
- **Placement classes** (CSS scoped to `.crm-demo` and `.agency-demo` on the page):
  `.cmhead.demo-pinned` insets its pin ahead of the title (`padding-left: 46px`); a `.cmfoot` pin
  sits on the footer's top edge at `left: 6px`, clear of the text above it; `.cpin-tr` puts a pin
  top right of a field, over the empty end of its label; `.cpin-inline` is an inline pin whose
  parent row is the tile; `.cpin-up` sits 16px higher, for a list whose first row has a tag at its
  right end; the chat card's pin sits in its dark title bar. Cards and the Agency
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
- **Annotations.** Each slide has numbered notes (`.demo-notes`) and a matching amber
  pin (`.demo-pin`) on the feature. Each note is 2 to 4 short bullets since 2026-09-16 (Max's call;
  it was one sentence per note before). On the page the notes row is
  hidden and each note pops up on its tile (2026-09-13, "Strip navigation and hover notes"); the
  standalone still shows the row.
- **Schedule slide order (2026-09-13, Max's call):** the lesson carrying the log buttons (pin 4 since 2026-09-14),
  Mira Okonkwo, is the first block of the day at 8:00&ndash;9:00. The Booking slide still shows her
  regular lesson on Tuesdays at 6 PM; not reconciled yet.
- **No pronouns for the user.** Copy says "the teacher", never she/her, and never names Dasha,
  and the product is called TeacherAID on the page. Max wants it to read as applicable to any teacher.
- **Screens use the app's own look** (IBM Plex, Newsreader, cool grey), not the Hub's cream.
  Classes are `ds-` prefixed; tokens are `--ds-` prefixed and live on `.dasha-demo`.

**Placeholder data only:** 18 fictional students, fictional employers (Harbor Piano, Maple Music
School), fictional rates. Never the real ledger.

**Copy still owed by Max:** the three benefit cards and the heading were
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
  Outcome cards sit below it (moved there 2026-09-13; copy unchanged).
- **Slide 1 is the new Dashboard (2026-09-15),** rebuilt from the Day view of
  `sprout-crm-next/components/DayBoard.jsx`, the Dashboard's rebuild that day. **Call it the
  Dashboard, never the Day Board** (Max's call, 2026-09-15), even though the app's code and
  CHANGELOG use that name. Its
  classes are the app's `db-` names, scoped under `.sprout-demo` on the page, and `data-nav`
  stays `dashboard`. The app's hatched rail on Sprout calendar rows is solid grey here, because
  the carousels carry no dashes. The old `.sp-stats`, `.sp-act` and `.sp-evrow` CSS is unused
  now, left in place.
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

### Session of 2026-09-17, last: five AI builder applications, two sent

Career work only; no site changes. One posting closed, two applications went out, two are drafted.

| Folder | Role | Status |
|---|---|---|
| `2026-09-clasp/` | Clasp, AI Labs Engineer | **Posting closed** before Max could submit |
| `2026-09-ease/` | Ease Health, Software Engineer (remote NYC) | **Applied Sept 17**, CV only |
| `2026-09-makai-labs/` | Makai Labs, AI Engineer (contract, $115k to $130k) | **Applied Sept 17**, CV + 2 form answers |
| `2026-09-brady-martz/` | Brady Martz, AI Prototyping Engineer (remote US) | Drafted |
| `2026-09-estrada-eci/` | Estrada Consulting, AI Solution Architect (remote US, W2) | Drafted |

- **Ashby postings render empty to a fetcher.** The text comes from
  `https://api.ashbyhq.com/posting-api/job-board/<org>?includeCompensation=true` (`descriptionPlain`).
  **Workable** has the same pattern: `https://apply.workable.com/api/v1/accounts/<org>/jobs/<shortcode>`.
  Both are now the way to read a posting, like the Workday JSON endpoint.
- **The Clasp materials became the base for the whole set.** `career/README.md` names the
  portfolio-led bullet letter at `applications/2026-09-clasp/letter.md` as the base for AI builder
  roles, by pointer rather than a copy, so the two shapes cannot drift.
- **Max's calls on the letter, which now define that shape:** one opening paragraph pointing at the
  portfolio, a short bullet per tool naming what it is and who uses it, then process bullets written
  to the posting's own duties with a colon after each label. **No worked examples in the process
  bullets: the portfolio is the example.** The tool bullets are never cut for page fit; page fit comes
  from the `Format:` line.
- **Each copy is tailored, not just renamed.** Makai leads its skills line with Python (their hard
  requirement) and says "benchmarked"; Brady Martz says "prototyped" and "non-technical users" and
  ends its documentation bullet on handoff; Estrada names Anthropic Claude outright, labels Claude
  Code as AI-assisted development, and reframes the walkthroughs as client demos.
- **Form answers, saved with their sources** in each folder's `notes.md`: the AI stack (models,
  harness, tooling, and why), the Sprout CRM project answer, and for Ease and Makai a production
  experience answer and an AI/ML tooling answer. **Every technical claim was checked against the
  repos**, and two were corrected: the program page is built from the artists' submissions with a
  template rather than rendered live, and there is no automatic email importer, only the
  `google-workspace` MCP used in a session.
- **`career/build.py` gained bullet support in cover letters.** `render_letter()` renders a body line
  starting with `- ` as a List Bullet paragraph, with a bold `**Lead:**` and links inside it.
- **Two standing rules from Max:** **always use the Oxford comma** unless grammar forbids it (now in
  `career/README.md` and in project memory), and every link opens in a new window.
- **Verified:** `check --all` OK on all twelve folders; every CV and letter one page; no letter body
  mentions another company; zero em dashes; the five portfolio deep links on the CVs tested live by
  Max. His LinkedIn headline no longer reads "Vibe Coder / AI Developer".

**Open:** Max's proofread of Brady Martz and Estrada. Brady Martz's data and privacy duty is not on
the CV (spelling out "row-level security" cost the page); it is interview material. Estrada prefers
cloud platform experience (Azure, AWS, GCP) that Max does not have, and Makai asked for a CS
background he does not have; neither is claimed anywhere.

### Session of 2026-09-17, last: Turing AI evaluator application sent

Career work only; no site changes. New folder `career/applications/2026-09-turing/`: Turing, Jr. AI
Evaluator, remote US contract, 16 weeks, $30 to $50/hr. **Max sent it Sept 17** through the Betterteam
form, with the CV and a short cover letter; the frozen copies are in `sent/2026-09-17/`.

- **The base AI roles CV does not fit an evaluator job:** it leads with tool building. The CV is built
  from the Innodata CV instead (evaluation first, Hudson Table for the music entries), with research,
  fact-checking and summarizing added, because the posting asks for them.
- **The Composer Compass entry is now the agent training story** (Max's call: the process, not the
  specifics). Six bullets: the protocol, benchmarking against finished pieces, fact-checking, the
  model comparison, prompt iteration across 16 versions, and the piece it guides now. An agent
  checked every claim against `composers-compass/training/`; the sources sit in the folder's NOTES.
- **Max's calls on claims, now a rule in `career/README.md`:** describe how a tool is meant to work,
  keep evaluation work at the process level, and leave off or reframe anything that reads as a
  misstep. So the named model errors, the Haiku failure and the "reduced only" hedge came out, and the
  UW CV's "theory library" line can stay.
  - Corrections the check found anyway: "76 checks across 6 harnesses" were app UI tests, not model
    evaluation, and identical-condition repeat runs do exist.
- **The Sprout Suite entry lists all four tools,** one bullet each (Max's call).
- **Eligibility:** "Can be a student or a fresher" is permission, not a requirement (a first read of the
  posting had it backwards). The real gate is an established Gemini App account with 10 or more
  education-focused conversations, validated before joining, not at application. Max has one Gemini
  chat and some notebooks; he is starting real study conversations and applying anyway.
- `check --all`: OK on all eight folders.

- **The cover letter** (added at Max's ask, then cut to about 240 words because it is optional): the
  posting's duties in order, the Compass named as a composition assistant that analyzes rather than
  generates, and one paragraph on finishing the master's in 2022 and turning toward AI since. Max cut
  "designed an evaluation, not just run one" as reading overqualified for a junior contract role.
- **No rate stated.** The form does not ask, and the posting names $30 to $50/hr.

**Next:** Max needs 10 or more genuine education-focused Gemini App chats before any onboarding check.
Open: his call on the new Sprout funder-research bullet and on "Microsoft Excel and Word" in Skills.

### Session of 2026-09-17, last: Innodata application sent

Career work, plus one site fix. **Max applied Sept 17** through Greenhouse to Innodata's Generative
AI Associate role (remote, part-time, $15/hr), with a CV and no cover letter. The frozen copy is in
`career/applications/2026-09-innodata/sent/2026-09-17/`.

- **New CV, built from the AI roles CV (Max's calls):**
  - Handshake AI comes first, then research and applied systems.
  - No music focus: Hudson Table replaces teaching and the studio job, and TeacherAID, the Composer
    CRM and Virtual Agency are cut.
  - The summary leads with writing and a humanities master's, because the job does.
  - Max confirmed two new lines: "edit copy for clarity and tone" and "Native English speaker".
  - The Composer Compass title links to `#composition`, and The Sprout Suite to `#tab-sprout`.
- **New rule (Max's, always):** every link opens in a new tab or window.
  - `career/build.py` now sets this on every docx link.
  - On `resume.html`, the two walkthrough links now open a new tab (commit `37e3dfa`, pushed).
  - A PDF can't force it; the viewer decides. Chrome and Edge open PDF links in the same tab unless
    the reader Ctrl-clicks.
- **`career/template.docx` had hidden link entries** from an older document (maxwellhenrymusic.com
  among them). They never showed in the text. They're removed, so new builds are clean; older
  folders lose theirs on their next rebuild.
- **Open:** the posting reads "Remote - Minnesota" and may only accept Minnesota residents.
- `check --all`: OK on every folder.

### Session of 2026-09-17, later: River Alliance and MEA application sent

Career work only. **Max emailed it on Sept 17** to jobs@wisconsinrivers.org, with both PDFs attached.
The submitted copies are frozen in `career/applications/2026-09-river-alliance-mea/sent/2026-09-17/`.

- **Final changes before sending (Max's calls):**
  - Resume: added "Support donor stewardship for a fundraising program that has raised over $1.5
    million to date." It's Sprout's all-time total, not money Max raised himself.
  - Resume: side margins widened from 46pt to 58pt (`Format: margins=58,36`).
  - Resume: "Team of three" cut. The letter keeps it, because it explains how much Max handles.
  - Resume: "agile project management" became "agile workflows".
  - Both documents: the LinkedIn link now reads just "LinkedIn".
  - Grammar fixes: a serial comma in the CRM bullet, and the run-on "and" in the letter's closing.
  - Letter: "your team" became "your teams", because the job serves two organizations.
- `check --all`: OK on every folder.

**Next:** the Savanna Institute application (Oct 4). Max hasn't proofread it yet.

### Session of 2026-09-17: River Alliance and MEA application locked

Career work only; no site changes. Everything below lives in `career/`, which is gitignored.

- **Research:** neither River Alliance nor MEA is against AI. Both fight unchecked data center growth:
  - River Alliance testified in Feb 2026 for a pause on construction.
  - MEA sued in July over Port Washington's environmental review, and sued Racine for data center records.
  - Neither says anything about using AI sustainably.
- **Max's call: no AI anywhere in this application,** in either the letter or the resume.
- **New letter strategy (Max's):**
  - It doesn't recap the resume. The opening gives one line on experience.
  - Then a story: Bay Area droughts, the Beloit farm, and Vermont Valley Community Farm.
  - Then character: a systems person who learns quickly, shown by the Salt + Charcoal kitchen story
    (dishwasher to cook in weeks). EveryAction and Neon are tied to the Sprout CRM strategy.
  - The close explains the part-time ask: Max composes and will be teaching music in Madison.
  - The numbering restarted at Max's voiced draft, and **v9 is final**.
  - "Michelin-reviewed" was dropped because it couldn't be confirmed.
- **Resume, final:**
  - Jobs in date order (Sprout, Music Major Records, Hudson Table), with the Composer entry and
    Interests cut.
  - The CRM became a Sprout bullet ("Led the project to build..."). Music Major Records gained an
    agile / Trello bullet.
  - Trello and Microsoft Office added to Tools. PMP (in progress) added under Certifications.
  - Availability now reads "Part-time, 20 to 24 hours a week; in person in Madison starting in October".
- **Standing rule (Max's call):** the Sprout CRM and Suite are dated 2026 on every resume from now
  on. The Savanna resume and the AI roles CV were updated. The sent WCO and WFAA copies keep 2025.
  The rule is recorded in `career/README.md`.
- **Lesson:** editing `letter.md` while Max had unsaved edits open made VS Code drop his edits once.
  Don't touch a source file Max has open until he says it's saved.
- `check --all`: OK on every folder.

**Open:**
- ~~Send River Alliance and MEA.~~ Sent Sept 17 (see above).
- **Confirm the PMP is still in progress** before an interview. It is listed on this resume.
- **Next:** the Savanna Institute application (Oct 4). Max hasn't proofread it yet.

### Session of 2026-09-16: every numbered note is a bullet list (pushed)

Max's ask: same info, faster to read. All 115 notes on `index.html` and the same 115 in the eight
`demo/` standalones are now 2 to 4 short bullets each, no end periods. Claude did the split; the
facts are unchanged.

- **Markup:** `<span class="demo-pin-n">N</span><div><ul class="demo-bul"><li>...</li></ul></div>`.
  A new note must use this shape. `initDemoPops()` still copies the note's HTML, now into a
  `div.demo-pop-txt` (a list cannot sit in a span).
- `.demo-bul` sets `list-style: disc` itself (Tailwind's preflight strips it) and colors the
  markers with the pin color. Added beside `.demo-note` in the page and every standalone.
- **Verified headless (1280 and 390):** every popover on every slide of all eight carousels shows
  its bullet list inside the screen; each standalone's notes row shows disc bullets; zero script
  errors; no em dashes added. Screenshots checked by eye.
- **Teaching page too:** `teaching.html` got the same treatment on the `teaching-page` branch
  (commit `d7dbc67`, not pushed), 69 of 69 popovers verified at 1280 and 390. Notes quoting a repo
  keep the quote word for word, split into a lead-in bullet and the quote. The worktree's
  untracked `demo/teach-*-demo.html` standalones were updated to match but left uncommitted,
  like the rest of that session's work there.

### Session of 2026-09-16: career files reorganized into `career/`, one-version rule, WFAA applied

Max's ask: organize the application scaffold now that there are six applications. Career work only;
no site changes.

- **Found:** the site served every career file publicly (for example
  `/career-search-master.md` returned 200), and the GitHub repo is public too.
- **New layout** (details in `career/README.md`): the five track docs in `career/tracks/`, the AI
  roles CV and base letter plus the ops resume in `career/base/`, and one folder per application in
  `career/applications/` (RISE-AI, WCO, Madison College, River Alliance and MEA, Savanna, WFAA). The
  two "Priority Applications" files were split into per-application `resume.md`, `letter.md` and
  `notes.md`, plus `applications/priority-three-overview.md`. The WCO letter drafts, answers and
  research moved out of the arts-education track doc into `applications/2026-09-wco/notes.md`.
- **One build script, `career/build.py`,** replaces the four `build_*.py`. It builds letters too, so
  every application now has its cover letter as a .docx and .pdf (the WFAA letter was never built
  before). Its template is `career/template.docx`, a copy of the site's CV docx, so Word locking the
  original no longer matters.
  - **Verified:** each rebuilt docx matches the old script's output paragraph for paragraph (text,
    styles, spacing, runs), except a 1pt gap under the AI CV's Skills section and Max's WFAA edits.
    All PDFs export at one page, except the WFAA resume (see Open).
  - **Word edits win:** a built docx is stamped with its source's time, and the build skips any
    docx saved later, so Max's Word edits never get overwritten.
- **The WCO `.docx` committed on Sept 10 was stale** (older wording, wider margins). The PDF matched
  the script. The rebuilt docx matches the PDF again.
- **Max's WFAA resume edits in Word** (the Union ensembles line, the Music Major Records and NYU
  bullets, a longer Tools line with Microsoft Office, Trello, Asana and Canva Pro) are in
  `resume.md`, with three typos fixed. His Word copy went to the Recycle Bin after the comparison.
- `Academic CV - UW Madison.docx` stays at the root: `resume.html` offers it as the download.
  `Curriculum - UW Madison.html` moved into the RISE-AI folder, so the site no longer serves it.

- **One-version rule (after Max once sent a resume with typos).** `career/build.py` now builds,
  checks and freezes: `check` fails on a docx that differs from its source, a stale PDF, anything over
  one page, or any extra file; every build and send logs to the folder's `versions.md`; `sent` freezes
  the submitted PDFs read-only in `sent/<date>/` and blocks rebuilds. Tested on a copy with a planted
  typo, a stale PDF and an "(old)" file: all caught. Stray copies in `Documents` and `Downloads`
  went to the Recycle Bin (the WFAA v3.1 letter, an old RISE-AI letter draft, a duplicate CV, and
  Max's Savanna letter, which he chose to drop for v2.1). The submitted RISE-AI letter and CV moved into
  `rise-ai/sent/2026-09-09/`. `Desktop\Resume and Cover Letters\` is ignored (Max's call).
- **Every application folder has a `job.md`:** posting and apply links, location and hours, pay,
  deadline, status, and a short summary. WCO has none: Max got the rejection on 2026-09-16.
- **Hudson Table rule:** see Career Context.
- **WFAA: applied 2026-09-16** through iCIMS, as PDFs. The frozen copies are in
  `career/applications/2026-09-wfaa/sent/2026-09-16/`.
  - The letter is v3.2 plus Max's proofread edits, with no portfolio link.
  - The resume, in date order: Sprout, Music Major Records, Hudson Table, teaching.
  - The Sprout Suite, CRM, Social Media Manager and Grant Finder link to their portfolio tabs; those
    links were tested live. The header has LinkedIn only.
  - Checked against the live posting. Word's spell check found 0 errors.

**Open:**
- **`career/` is gitignored (Max's call),** so it lives only on disk and in OneDrive, with no version
  history. The public GitHub history still holds every career file committed before 2026-09-16.
- **Next: River Alliance and MEA** (**sent Sept 17**, see above), then
  Savanna Institute (Oct 4), drafted with Hudson Table and not proofread yet. Update each letter's `Date:` line on
  send day.
- **WFAA follow-up:** if asked where he lives now, Max can interview in person on about a week's notice
  and start as early as Oct 19.
- **Open question:** does the AI roles CV follow the Hudson Table rule? It still lists teaching and the
  studio.

### Session of 2026-09-15: cover letters and resumes for the three priority applications (pushed)

Career work only; no site changes. Commits `f049f07` through `a0ed07e`. The files named below were
reorganized into `career/applications/` on 2026-09-16.
Everything lived in
`Priority Applications Cover Letters.md` (comparison, facts, template, letters, claim maps) and
`Priority Applications Resumes.md` (text source plus NOTES), built by `build_priority_resumes.py`.

- **Compared the three postings** (WFAA, Savanna Institute, River Alliance and MEA) from the live
  text, then one template: hook, breadth, shared core proof, job fit, close.
- **Letters:**
  - **Savanna v2.1:** Max's own edit plus a fix pass. Addresses every required qualification, one page.
  - **River Alliance and MEA v1:** in Max's voice, with the water hook, "coming back to Madison" and an
    Oct 19 start.
  - **WFAA v3.1, final (Max's call):** a separate letter built on his UW story (Terrace summers,
    alumni family, 2014 Big Ten rugby title, shows at the Union). The driver's license line was
    restored because the posting requires it.
- **New facts from Max, recorded in the letters file:**
  - Family and farm: summers on his grandparents' farm in Beloit; his aunt and uncle Barb and Dave
    Perkins founded Vermont Valley Community Farm and were Wisconsin CSA pioneers (not on Savanna's
    site). He grew up in the Bay Area with droughts and wildfires.
  - Sprout: over $1.5 million raised and around 3,000 all-time donors, in a CRM he built from scratch
    to replace paid software, with emails sent through Campaign Monitor.
  - UW: his dad and dozens of family members are alumni.
- **Framing calls (Max's):**
  - Play up the entrepreneur breadth (full for Savanna, medium for WFAA, light for River Alliance).
  - Include AI, framed as understanding the workflow, one mention, never the lead. Claude advised
    omitting it for River Alliance and MEA: MEA sued over the Port Washington AI data center in July
    2026, and River Alliance testified for a data center pause. Max chose to pair it with his concern
    about AI's water use instead.
  - Letters read as a Madison candidate but never state residence. Max will move once hired, can
    interview in person on a week's notice, and can start Oct 19. Resume headers read "Madison, WI".
- **Resumes:**
  - One page each, checked by eye in the exported PDFs. Savanna leads with development operations;
    River Alliance is written at assistant level; WFAA opens with UW. The WFAA resume has no AI
    wording, matching Max's letter edit.
  - The docx and PDF outputs are **not committed**, so Vercel does not serve them.
- **Word export lesson:** a hidden COM instance hung on the OneDrive copy. It worked after copying
  the docx to the scratchpad and setting `DisplayAlerts = 0`. Only the new WINWORD process was
  killed; Max's open Word window was left alone.

**Open:**
- River Alliance letter (due Sept 27): keep the data center specifics? Add the portfolio link? Put
  Vermont Valley back in?
- Resumes: Microsoft Office on the WFAA and River Alliance Tools lines? Is the PMP still in progress
  (it would help Savanna)?
- LinkedIn headline still reads "Vibe Coder / AI Developer"; every resume links to it.
- Max has not reviewed the resumes yet.

**Next:** Max reviews the resumes and answers the open calls. Then submit River Alliance and MEA by
email (subject "Development and Administrative Assistant Search") by Sept 27, Savanna on PinPoint by
Oct 4, and WFAA on iCIMS. Log each submission in `career-search-arts-education-track.md`.

### Session of 2026-09-15: notes open above their pin, on every carousel (pushed)

Max's ask: a note popping up under its pin covered the feature it describes. Every carousel's note
now opens **above** its pin. One change in the shared `initDemoPops()`, so all eight carousels on
`index.html` get it, and the same change in `teaching.html`, committed on the `teaching-page`
worktree as `ba6992f` (branch still unpushed, so the live site only shows the `index.html` half).
**A future re-transplant or merge must not take the old below-the-pin `placePop()` back.**

- **`placePop(mayScroll)`** places the note at `pin.top - height - 8`. The below-the-tile fallback is
  gone.
- **The ceiling is the page's fixed chrome** (`stickyOffset()`: nav + tab bar + tool row), not the
  carousel's own pinned strip and title card. A note may pass over that strip, which is the lesser
  harm, and it is the only way a pin at the top of a tall tile can have its note above it at all:
  the title card scrolls with the page, so the gap under it never grows. The pop's z-index (29) is
  already above the strip (27) and the title card (25), and below the tool row (30).
- **When even that leaves no room, the page scrolls to make it** (Max's call, 2026-09-15), instead of
  dropping the note back under the tile. Only the opening call may scroll: `showPop(info, noScroll)`
  passes `mayScroll`, while the scroll and resize listeners call `placePop()` bare, or the page would
  yank itself back while the user scrolls. After the scroll it re-places on the next frame, because
  the pinned layers settle a frame later.
- **A "More below" chip leaves room for the note.** It opens the note first, then scrolls by the
  note's height plus the old gap, so the chip's own landing does not put the pin back under the
  ceiling.
- The entry animation now slides down from above (`translateY(-4px)`).
- **Verified headless (Playwright, 1280 and 390): 115 of 115 pins on `index.html`**, every one on
  every slide of all eight carousels, reached by stepping with the `is-next` control: the note sits
  fully above its pin, below the fixed chrome and inside the screen; zero script errors.
  **`teaching.html` 69 of 69** at 1280. **Dock chips 5 of 5** at both widths: the chip lands its pin
  on screen with the note above it. Screenshots checked by eye.
- The `demo/` standalones have no popovers, so they are unchanged.



Max's ask: the Sprout CRM carousel's Dashboard slide shows the new dashboard sprout-crm-next
shipped the same day. **Max's call: it is still the Dashboard, not the Day Board,** so the page never
uses that name, though the app's code and CHANGELOG do.

- **Slide 1 in `index.html` and `demo/sprout-crm-demo.html`** now rebuilds the Day view: the header
  summary with Day / Week and + Add task, the day bar, On the calendar (Co-Working on the Sprout
  calendar, a run-of-show call), five tasks in priority order (three done, struck through with
  Undo; Imani Shaw 4d late and moved at midnight), then the week meters by category in Google
  Calendar colors, the Sprout calendar total and the weekly bank. The nav entry still reads Dashboard.
- Same placeholder world as the other slides: Tuesday, September 1, 2026, with Rosa Delgado, Imani
  Shaw, Quiet Hours Social, Maya Chen and Kai Brennan.
- **5 pins:** the header, the calendar rows, the task list, the week meters, the weekly bank. The
  title, state line and notes are Claude's drafts; Max has not called them.
- Swapped in by a scratchpad script (slide range, CSS before the ContactDetail block, nav label).
  `git diff --stat` confirmed nothing else moved.
- **Verified headless (1280, and 390 with touch): 57/57.** Five slides, the nav lit and reading
  Dashboard, two columns at 1280 and one at 390, 5 pins and 5 notes, every pin's tile opens its
  popover in view, no pin clipped, no overflow, no dashed borders, the next cue walks all five
  slides, the strip stays one line (51px), zero script errors, em dash counts unchanged. The
  standalone shows its notes row. Screenshots checked by eye.

**Open:** Max's copy call on the slide's title, state line and five notes.

### Session of 2026-09-15: the Teaching page, built on branch `teaching-page` (NOT on main, NOT live)

**Where it lives (Max's call, 2026-09-15): off the live site until he says it is final.** Branch
`teaching-page`, checked out as a git worktree at
`C:\Users\maxwe\OneDrive\Desktop\Claude\Apps and Tools\AI Tool Portfolio - teaching-page\`. **Build
there, not in this folder.** The branch commit holds `teaching.html` plus the Teaching nav link (and
the phone name hide) on `index.html`, `about.html` and `resume.html`. Main has none of it, so the live
nav is unchanged. The branch is not pushed. Merging it into main is what puts Teaching on the live
site: only on Max's word.

Built from a two-round wireframe (`docs/wireframes/2026-09-15_teaching-page.html`, artifact
https://claude.ai/artifact/Qjp5iLNzACk5AVs9sGmU7c) for the UW-Madison RISE-AI committee, and as the
base for the final-round live class. Max's calls and the accuracy notes also sit in
`career-search-academic-track.md` under Open Items.

- **The page:** "Music and AI Integration". Hero, a 15-week map (weeks 1 and 2 are these topics; the
  selected topic lights its later weeks, named from the AIM 101 curriculum draft), a sticky topic tab
  bar, then one card per topic: heading, a 50-minute run-of-show bar, a carousel, three cards
  (Objective, Try it, Check yourself) and a "Goes deeper in" line. Contact block and footer.
- **Four topics, 54 slides:** How AI works (12), Tools and workflows (11), Building with AI (12), and
  How the tools were built, with Composer Compass (9) and TeacherAID (10) as tool tabs.
- **Same carousel system as `index.html`, copied** (one file per page): the `[data-demo-panel]`
  initializer, pinned strip and title card, step chips, the next cue, pin popovers, the dock, and the
  GA events (`tab_click`, `tool_click`, `slide_view`, `note_view`, `link_landing`). Slide content is
  `t-` prefixed under `.teach-demo`. The GA tag is in the head.
- **One deviation from the wireframe:** no separate practice rail. In Building with AI and both build
  stories the strip entries are the practice names (Memory, Version control, Effort, Wireframe, Verify,
  Evaluate, Guardrails), so the lit entry is the practice. Every practice lights at least once across
  the two builds.
- **Build-story copy is verbatim from the repos**, checked by a research agent against file and line,
  with em dashes replaced by colons. Each slide's caption carries its source. Do not reintroduce:
  "handwritten" or "paper" for TeacherAID (not in the repo); "76/76" (the log says "76 checks across 6
  harnesses"); any claim that removing data fixed prescriptive suggestions (the v5.9 rewording did;
  Training Session 86's count removal fixed counting). TeacherAID visuals use placeholder data and
  "[the teacher]", never the name, employers, course codes, students or pay.
- **Nav on all four pages** gained Teaching after CV. At 360px the row then overflowed on every page, so
  the `mhperkins.dev` name hides below 640px (`hidden sm:inline`) and the links take `ml-auto`, on
  index, about, resume and teaching.
- **The 15-week map is 8 + 7 columns on desktop;** fifteen columns broke week names mid-word.
- **Verified headless (Playwright, 1280, and 390 with touch): 69/69.** Every topic and tool shows; the
  map lights the right weeks; every pin has a note; every slide is reachable by clicking only the next
  cue, with no cue on the last slide; every desktop pin target opens its popover; no sideways scroll;
  zero script errors; zero em dashes. **Nav 12/12** at 1280, 390 and 360 on all four pages (one line,
  inside the screen). Screenshots checked by eye.
- **Preview:** https://ai-portfolio-landing-page-qxbmfzoiu-mhperkins-projects.vercel.app/teaching.html
  (Vercel login).

**Open:**
- **Next conversation:** open the worktree folder and keep building there. First Max's copy review of
  all four topics, then the final-round presenter file. Merge `teaching-page` into main only when Max
  says the page is final; that merge is what adds Teaching to the live nav.
- **The branch has two commits beyond the page itself,** both mirroring changes main shipped:
  `ba6992f` (notes open above their pin) and `d7dbc67` (notes are bullet lists). A later session
  in the worktree also left `demo/teach-*-demo.html` and its own `CLAUDE.md` edits uncommitted there;
  that is the branch's copy of this file, not main's.
- **The preview above is a snapshot** deployed before the move. Deploy new previews from the worktree
  (`vercel deploy`, never `--prod`; its `.vercel/` link was copied in, since that folder is gitignored).
- The headless suites live in this session's scratchpad and are gone with it. Rebuild them from the
  checks listed above if needed.
- All copy is Claude's draft from the wireframe and the research; Max has not called it.
- The final-round presenter file (half Tools and workflows, half How the tools were built, frame D of
  the wireframe) is not built. Activity timers are static text.

### Session of 2026-09-15: career leads audit and priority list (pushed as `36eac79`, `57911c5`, `1e51836`, `73ba557`)

Career work only; no site changes.

- **Audit.** Every lead in the three track docs was loaded live on Sept 15 (four parallel agents,
  one per track slice). Employer ATS links replaced aggregator links where one exists, and each
  track doc now lists verified job boards for its search type.
  - **Dropped:** Careerswift AI and Workflow Automation Specialist (removed Aug 13; the Himalayas
    "expires Sept 16" copy was stale), Noodle Prompt Systems Engineer (closed), CIMA Consulting
    (apply link 404s), NewRocket, Back At You and Pearson (no posting exists), Wheelhouse Studios
    (404), Historical Society Learning Facilitator (only a LinkedIn copy left).
  - **Academic:** none of the Sept 14 leads closed. UNO, Berklee and NC State are now posted; UCSC
    Theory & Composition pool (JPF02104) and UCSD Temporary Lecturer (JPF04495) are new. RISE-AI is
    still open and its degree line accepts a Master's in Music.
  - **Correction to the Sept 14 Madison College entry below:** R0002302 *is* the Video Audio Design
    pool. Its posting title changed; only the URL keeps the Visual Communications name.
- **Verification lessons.** Himalayas keeps expired listings, so confirm on the employer's page.
  Lever pages block the fetcher but `api.lever.co/v0/postings/<org>` works, like the Workday JSON
  endpoint. The `r.jina.ai/<url>` reader proxy gets past 403s on some org sites (Savanna Institute,
  River Alliance). Midwest Environmental Advocates sits behind a security check.
- **Priority list (Max's call),** at the top of `career-search-arts-education-track.md`:
  1. WFAA, Engagement Program Coordinator (Madison, FT, hybrid, no deadline).
  2. Savanna Institute, Development & Communications Manager (remote, $62k to $68k, deadline Oct 4;
     asks 3+ years, so win on scope, never claim years).
  3. River Alliance of Wisconsin and Midwest Environmental Advocates, Development and
     Administrative Assistant (Madison, PT, $20/hr, priority deadline Sept 27, start Oct 19).
- **The connected Gmail MCP is the Sprout work inbox,** not Max's personal Gmail, so application
  confirmations and rejections are not visible to Claude.
- Committed a Composer Hub session's uncommitted GA notes on their own as `7f1b11e`, so they did not
  ride inside this session's commits.

**Open:**
- ~~No materials yet for any of the three priorities.~~ Drafted later the same day; see "cover
  letters and resumes for the three priority applications" above.
- ~~WCO: materials ready, still not logged as submitted.~~ Rejected (Max, 2026-09-16).
- Check by hand: Overture's education coordinator role; whether Careerswift Implementation
  Specialist is really open (its Ashby page shows only a title); UMKC's "or equivalent professional
  experience" clause.

**Next:** by deadline, the River Alliance and MEA application first (Sept 27), then Savanna (Oct 4),
then WFAA.

### Session of 2026-09-14, evening: nav, portrait, Contact landing (pushed as `63fd62b`, `ebc5895`, `e3d5142`, `cbab937`)

All at Max's call, all verified headless.

- **About and CV navs read Portfolio · About · CV · Contact** (`63fd62b`). One "Portfolio" link to
  `index.html` replaces Composer Hub and Sprout Suite, which named only two of three tabs and both
  just went home. Shows at every width; one line at 1280, 390 and 360.
- **Color portrait beside the About text** on `about.html` and the home page's About section
  (`ebc5895`). It is the on-stage photo from the composer portfolio's About section, **not** the
  black and white piano hero. Copied to `images/maxwell-portrait-500.webp` and `-800.webp`. A
  `md:grid-cols-[2fr_3fr]` grid: photo left at desktop (374 by 468px), stacked above the text on a
  phone. Alt text says Maxwell Perkins, not the stage name Maxwell Henry.
- **About page name in all caps** (`e3d5142`): `uppercase` on the `h1`; the text stays "Maxwell Perkins".
- **Contact links land on the section top** (`cbab937`). `#contact` was not in `cardToTab`, so the
  browser's own jump hid the label and heading under the fixed nav and pinned tab bar.
  `navigateToHash()` now handles `contact` first: logs `link_landing`, strips the hash, and after
  150ms scrolls the section to 16px under nav plus tab bar. The tool row is deliberately not
  counted (it releases at the end of its tab panel). `#contact` also has a matching
  `scroll-margin-top` so the native jump lands close before the correction. Verified at 1280 and
  390 from a direct `index.html#contact` load, the home nav link and the CV nav link: section top
  at 130px (150px at 390), label clear of the tab bar, zero script errors.

**Open:** the divider above "Get in touch" on `about.html` renders bright white instead of faint.
It predates this session: `border-white/8` is not a Tailwind opacity step, so the border falls
back to the default light grey. Max has not called it.

### Session of 2026-09-14: Madison College music instructor pool application (pushed as `fb50156`)

Career work only; no site changes. Ran alongside the sessions below.

- **Posting verified through Workday's JSON endpoint.** The Workday page renders empty to a fetcher,
  but `/wday/cxs/<tenant>/<site>/job/<path>` returns the full posting text. Reuse it for any Workday
  posting. PT Instructor Pool, Music (R0002307): a per-course part-time pool, rolling, closing about
  Jan 31, 2027. The courses are general education surveys: Black American Music, Music Appreciation,
  Music Theory Fundamentals, History of Pop and Rock Music, World Music. The M.M. meets the minimum.
- **CV and cover letter drafted,** one page each. Sources `Madison College CV.md` and `Madison
  College Cover Letter.md`; `build_madison_college.py` builds `Maxwell Perkins CV - Madison College`
  and `Maxwell Perkins Cover Letter - Madison College` (`.docx`, with PDFs exported through Word).
  Proofread from the docx text and the exported PDFs. The framing calls sit in the academic track's
  Application Log: teaching first, no Compass lead, no World Music or Black American Music claims,
  software in plain language for the posting's educational technology line, no portfolio link. Neither
  document makes the unsupported Compass claims listed in the AI roles entry below.
- **These docx and PDF files are committed, so Vercel serves them publicly.** The AI roles session
  below left its outputs uncommitted for that reason. Max has not picked a rule. Untracking them now
  would stop Vercel serving them but would not remove them from git history.
- **The PDF export quit Word without checking for open documents** (`$w.Quit()` on the COM
  instance), before the AI roles session found Max may have Word open. Nothing reported an error. The
  build reads `Academic CV - UW Madison.docx` as its template, which that session found locked while
  open in Word; `build_ai_cv.py`'s fallback to the Community Engagement docx is the fix if a rebuild
  fails.
- The academic track's Madison College lead linked the wrong pool (Visual Communications, R0002302).
  Corrected to the music pool. The Video Audio Design pool is still unchecked.

**Open:**
- Unofficial transcripts from NYU and UW-Madison (Max).
- Max's calls on three letter lines: "Madison College would be my first college classroom", the
  Black American roots line, and "Dear Hiring Committee" (the Associate Dean's name did not turn up).
- The LinkedIn headline, shared with the AI roles open item below.
- Whether generated application PDFs stay committed.

**Next:** Max makes the letter calls and pulls transcripts, then applies through Workday and logs the
date in `career-search-academic-track.md`.

### Session of 2026-09-14: job search sweeps, AI roles CV and cover letter (pushed)

Career work only; no site changes. Commits `808437c`, `300857d`, `3a9ba35`, `9a7a1f8`. A parallel
session shipped the GA and About work below at the same time.

- **Three live job sweeps, each logged in its track doc** (verified on Sept 14 unless marked):
  - **Academic music tech and AI, national** (`career-search-academic-track.md`, Leads): no
    RISE-AI-style cluster hire is open this cycle. Best fits: UMKC Assistant Professor of
    Composition (technology-integrated; names AI-assisted creative practice; rolling review), UCSC
    Assistant Teaching Professor, Sound and Media Art (M.M. qualifies; review Oct 12), and the UCSC
    Electronic Music Lecturer Pool (its courses include "AI and Music").
  - **Madison arts admin** (`career-search-arts-education-track.md`, Madison Leads): nothing as close
    as WCO. Best: Children's Theater of Madison Education Assistant, MSCR Arts Field Supervisor, WYSO
    Social Media Coordinator. Madison Community Foundation's Office Coordinator is interviewing now.
    Overture's Education & Community Engagement coordinator role is **unverified**: its job board
    blocked every fetch.
  - **AI tool, workflow and low-code roles, remote and Madison** (`career-search-master.md`, Current
    Leads): about 30 roles. Top: AARP Engineer I, AI Agents; Anthology GTM Engineer I; Valsoft AI
    Automation Engineer; a Madison hybrid Founding Forward Deployed Engineer through Carex. The
    track's location rule changed from NYC hybrid to Remote or Madison.
- **AI roles CV** (`AI Roles CV.md`, `build_ai_cv.py`): one page, the academic CV reordered for AI
  roles, with every technical claim checked against the source repos (NOTES in the md). Max chose
  this over a resume a job database site suggested, which had copied the pre-fix CV typos and listed
  Python first. Outputs `Maxwell Perkins CV - AI Roles.docx` and `.pdf`, **uncommitted** because
  Vercel would serve them publicly. The PDF exports through Word COM from PowerShell; only quit Word
  when the script's instance started with no documents, since Max may have Word open.
- **Word locks a docx while it is open.** `Academic CV - UW Madison.docx` was locked during the
  build, so `build_ai_cv.py` falls back to the Community Engagement docx, which has the same styles.
- **AI roles cover letter** (`AI Roles Cover Letter.md`): a base letter in Max's shape. His AI
  story, then the Composer Hub and its training protocol (his biggest project), then the Sprout
  Suite and TeacherAID, then a company paragraph swapped per posting. About 340 words before that
  paragraph. NOTES map every claim to evidence and include an example paragraph for AARP.
- **What the composers-compass training record does and does not support** (checked for the
  letter; applies to every application):
  - Supported: 16 system prompt versions, one-variable A/B experiments, a scored v1 rubric, a
    Sonnet / Haiku / Opus comparison, independent runs reaching the same structural decisions, and
    "tested on my last three pieces".
  - Not supported: a theory library in the RAG pipeline (only a `score_sidecars` collection
    exists), numeric scores on the six-dimension v2 rubric, "used it to write my last three pieces"
    (only the bass fugue was written with the protocol), blind scoring, repeated identical runs.
  - The AI CV was corrected. **The UW-submitted CV still says "theory library", and the UW letter
    says "used it for my last three pieces" and "two years in prompt engineering" (Handshake is one
    year).** Bring corrected versions to an interview.

**Open:**
- Max's calls on the AI CV: is the n8n digest still running (written past tense), and is PMP still
  in progress (omitted).
- LinkedIn headline still reads "Vibe Coder / AI Developer"; both new documents link to it.
- Company paragraphs for the top AI leads. Careerswift's AI and Workflow Automation Specialist
  posting expires Sept 16.
- Check the Overture coordinator role by hand. The WCO application has not been logged as
  submitted since Sept 10. (Rejected, 2026-09-16.)

**Next:** apply to the top AI leads with the CV and letter, writing a company paragraph for each.

### Session of 2026-09-14, late: Google Analytics and click tracking (pushed as `9852747`, `7a6bd07`)

**Google Analytics.** The GA4 Google tag `G-ENBE32TRFZ` sits first inside
`<head>` on `index.html`, `about.html` and `resume.html`. It is deliberately left off
`composer-hub.html` (it redirects instantly to `index.html`, so a tag there would count every visit
twice), the `demo/` standalones (unlinked iteration sources) and `Curriculum - UW Madison.html`. A
new public page needs the same snippet.

**Click tracking (added 2026-09-14, Max: "the only thing that matters").** GA only counts page
views, and the portfolio is one page, so `index.html` sends events through `trackEvent()` in the
main script:

| Event | When | Parameters |
|---|---|---|
| `tab_click` | a main tab button | `tab_name` |
| `tool_click` | a tool tab button | `tool_name` |
| `slide_view` | any user slide change in any carousel (strip, chip, rail, Blueprint tag, arrow keys), never the initial `show(0)` and never the slide already showing | `carousel`, `slide_number`, `slide_title` |
| `note_view` | a numbered note stays open 1 second; once per slide and note per page load | `carousel`, `slide_number`, `slide_title`, `note_number`, `note_text` (first 100 chars) |
| `link_landing` | arrival through a hash link (`#grant`); `navigateToHash()` strips the hash before GA reads the URL | `link_hash` |
| `email_click` | a `mailto:` link | none |

- Slide events live in both `turn()` functions, not `show()`. Note events live in `initDemoPops()`.
- `carouselName(root)` names a carousel for its tool button, or its tab button on TeacherAID.
- The parameters only reach GA's standard reports once registered under **Admin → Custom
  definitions** as event-scoped custom dimensions. Realtime and DebugView show them without that.
- Verified headless with Google blocked, reading `dataLayer`: every event above fires with the right
  parameters, a note shown under a second logs nothing, a repeat note logs nothing, zero script errors.
  Both commits are confirmed live on the production URL.
- `about.html` and `resume.html` send page views only. GA's enhanced measurement already covers the
  CV DOCX download and the GitHub and LinkedIn links.

**Resolved later on 2026-09-14 (from a Composer Hub session, through the GA Admin API):**
- **Why Max saw no data.** The property that owns `G-ENBE32TRFZ` is named **"Brooklyn, NY - Research"**
  (`properties/297328055`), under the GA account "Asauciation". Nothing in its name says portfolio,
  so Max was likely viewing a different property. Pick that one in the GA web UI.
- **Custom dimensions registered** by script, all event-scoped: Tab name (`tab_name`), Tool name
  (`tool_name`), Carousel (`carousel`), Slide number (`slide_number`), Slide title (`slide_title`),
  Note number (`note_number`), Note text (`note_text`) and Link hash (`link_hash`). Three
  composer-site dimensions (`click_label`, `click_context`, `click_target`) Max had registered here
  by mistake were archived, which is GA's only form of removal. GA does not backfill: the details
  appear only for events after registration, 24 to 48 hours later.
- **Claude can read this property directly.** A read-only user-scope MCP server, `ga-ai-portfolio`
  (Google's `analytics-mcp`), runs reports and realtime queries on it. Setup, credentials and
  re-auth steps are in the Composer Hub project memory `google-analytics-mcp-servers.md`.

**Next:** once data arrives (after Sep 15 to 16), break `tab_click`, `tool_click`, `slide_view` and
`note_view` down by their dimensions; then the open copy items in the 2026-09-13 session below.

### Session of 2026-09-13, last: suite banners removed, tiles under the carousels (pushed)

At Max's call, the suite banners (label, tool names, three bullets) are gone from the Hub,
TeacherAID and Sprout tabs, along with the `.suite-banner` CSS. Each tab now opens straight on its
tool row, or on its card for TeacherAID. Nothing in the script measured the banner. Verified
headless at 1280 and 390: no banner on any tab, all three tabs switch, carousels initialize, zero
script errors.

Then, also at Max's call, **each tool's three tiles moved from above its carousel to below it**, on
all eight tools (the Hub benefit cards, TeacherAID's, and Sprout's Problem / Solution / Outcome).
Headings stay above the carousels. The tile grids trade their bottom margin for `mt-8`. Page only;
the `demo/` standalones never had the tiles. Verified headless at 1280 and 390: on every tool the
grid is the carousel's next sibling inside the same card, holds three cards and renders below the
carousel, and every carousel still steps; zero script errors.

**2026-09-14: every dashed line in the carousels is solid now** (Max's call), in `index.html` and all
eight `demo/` standalones: the hint pills, the `is-next` cue on strips, chips and rail groups, the
"Hover a number" pill, future rail pills, the Compass back edge (its unlit dash pattern is gone), and
in-slide dashes (upload and drop zones, chart gridlines, the add-code form, empty states). The 1px
dotted row dividers (Compass `.drule`, CRM `.cprot-row` and `.cans`, Agency `.adoc-tbl td`) became
solid too, since at that size they read as dashes. Verified headless: no rendered element on the
page or any standalone has a dashed or dotted border or outline, and no SVG stroke has a dash
pattern; zero script errors.

**2026-09-14: hints moved** (Max's call), page and standalones. Compass: "Click through the process"
sits under the Intake group instead of top right. Hub CRM, Agency and TeacherAID: "Click to step
through" sits 12px after the last tab instead of at the far end of the strip (page rule scoped to
those three roots; the Sprout strips keep theirs at the far end).

**2026-09-14: TeacherAID Schedule slide rebuilt for the app's Add button and lesson menus** (Max's
call), page and standalone, grounded in dasha-board's `ScheduleTab.tsx`, `AddMenu.tsx`,
`LessonRow.tsx` and `LessonMenu.tsx`. The "Add to this day" card is gone, because the app replaced
it with one **+ Add** button in the Schedule header. Every lesson row carries a &#8943;, and Nora
Castellanos's is drawn open, the &#8943; highlighted in the pin color: `.ds-popmenu` pops out beside it
into the right column with the app's menu for a lesson not yet logged (the four status buttons,
Follow-up, Reschedule, Notify family, Open student; no What you worked on, which the app shows only
once a lesson is Completed). **Later on 2026-09-14 (Max's call):** Nora's lesson went back to
unlogged so the open menu shows every option, Reschedule included, and Clara Voss's lesson became
the completed one, with a progress note. The day's totals did not change (1h 30m billable, 3 of 5
logged), because Clara's 45 minutes replace Nora's. It started on Clara Voss's row and moved up to Nora's the same day at Max's
call, so its blurb sits higher on screen. `.ds-frame` clips overflow and the week card sits above,
so the menu starts 126px above the row with its caret level with the &#8943;, and tracks the right
column's width; below 760px it drops in under the lesson. Sam Whitaker's excused row shows the app's Reschedule button instead of the
old "Makeup Thursday?" prompt. The "Why this screen is first" note came out to make room for the
menu. Pins are now 1 + Add, 2 the catch-up card (new blurb: missed lessons collect by day and
Continue opens one short review), 3 the week meters, 4 Mira's lesson, 5 the menu. Copy is
Claude's draft; Max has not called it. The move to Nora's row briefly rode inside a parallel
session's local commit, which that session rewrote (`6cec73c`) without it before pushing, so the
page half shipped a commit after the standalone. Check `git status` before trusting a sweep.

**2026-09-14, later (Max's calls):**
- **Sprout tools have headings, no badges.** The "Live · Actively Used" and "Live · Functional V2"
  status tags are gone, and each Sprout card opens on a `tool-h` heading like the Hub and TeacherAID
  cards: CRM "Every relationship, event and follow-up in one place", Grant Finder "From funder
  research to a finished application", Social Planner "Draft it, approve it, publish it to
  Instagram", Campaign Tracker "See which flyers and links bring people in". Claude's drafts; Max
  has not called them. The `.status-*` CSS stays, because the component table still uses it.
- **The hero's skill tags** gained VS Code, right after Claude Code.
- **The top nav is more prominent** on `index.html`, `about.html` and `resume.html`: the links wear
  the hero name's white, bold, with wider letter spacing, and turn brand green on hover. The
  `text-sm` utility came off the links, because the Tailwind CDN's styles land after the page's and
  would win. On About and CV the current page's link is brand green (`.is-current`). **Their Composer Hub and
  Sprout Suite links became one "Portfolio" link to `index.html`** (Max's call, 2026-09-14: the two
  named only two of three tabs once TeacherAID arrived, and both just went back to the home page).
  It shows at every width, so phones get Portfolio, About, CV and Contact. Verified headless at
  1280, 390 and 360 on all three pages: one line, inside the screen, zero script errors.
- **The Compass rail's Sketch pill reads Sketch/Draft** (Max's call), page and standalone, and its
  group's aria-label says "Sketch and Draft". Slide 4's Sketch node header still reads Sketch,
  because that node sits beside a separate draft card.
  - **The wider label exposed a rail bug, fixed in both copies.** On the page the rail is 836px and
    its content was already 850px, so `show()` scrolled it 14px after drawing the back edge; the new
    label made that 46px, which clipped Score and slid the edge and the "Click through" hint off
    their pills. On a phone the edge was already hundreds of pixels off. Now pills take
    `7px 10px 7px 8px` padding and `.demo-rail-edge` a 12px floor (was 18px), so the page rail fits
    without scrolling, and a scroll listener on `.demo-rail` redraws the back edge (rAF-throttled).
    `.demo-rail-svg` clips to the field (`overflow: hidden`), so a curve under a scrolled rail stays
    inside it.

**2026-09-14: hero slimmed to one band** (Max's call: the carousels should sit much higher). The
three-line poster (Maxwell Perkins / DEVELOPMENT / PORTFOLIO / AI Developer, plus a 5x2 tag grid)
became a `.hero-band` aligned to the nav's edges: a green mono "Development Portfolio" eyebrow,
"Maxwell Perkins" with "AI Developer" in green under it, and the ten skill tags at 11px on the
right (stacked under the name below 760px). The tab bar's bottom margin went from 40px to 16px.
The bouncing `#scroll-btn` is gone (markup, CSS, script): it only existed to jump past the tall
hero, and once the carousel sat on the first screen it covered the "More below" dock. Verified
headless: tab bar 444px to 214px from the top at 1280; Compass carousel starts at 561px; no
horizontal overflow at 390 (the old hero H1 overflow is gone); zero script errors.

**2026-09-14: tech tag rows removed from every tool card** (Max's call), all eight tools. Titles,
taglines and the Sprout status badges stay. The Hub and TeacherAID title blocks went from `mb-3`
to `mb-5` so the heading does not crowd them. The hero's ten skill tags are not affected. Do not
put the per-tool tag rows back. Verified headless: zero `.tech-tag` inside any `.tab-panel`,
Compass carousel now starts at 521px at 1280x800, zero script errors.

**2026-09-14: card titles removed, card headings enlarged** (Max's call: the tool tabs already
name each tool). All eight cards lose their `h3` title, and the Hub and TeacherAID cards lose the
tagline under it ("The composing tool" and so on). The Sprout cards keep their status badge,
centered alone above the carousel. The four headings ("A visualized creative process, not a chat
window" and the rest) are now `.tool-h`: Barlow Condensed 700 to match the hero,
`clamp(1.35rem, 3.6vw, 2.35rem)`, balanced wrap. The Google Fonts link gained Barlow Condensed
600 and 700 (it loaded only 300 and 900). At 1280 the two long headings run about 89% of the card
on one line; "Your virtual team" is short and stays short. Do not bring the card titles back.

### Session of 2026-09-13, late: TeacherAID on the CV, CV docx typos fixed (pushed)

**TeacherAID added to all three CV copies** (`0b98920`, `16bb5fd`): `resume.html`,
`Academic CV - UW Madison.docx` and its `.md`, under Applied Systems after the Sprout Suite. A note
line, four bullets (one-tap lesson log, per-employer locked pay periods, booking link and income
plan, scheduled email summaries with AI observations), and on the page a walkthrough link to
`#tab-dasha`. Copy is Claude's draft from the tab's cards and the dasha-board repo; Max has not
called it. Same rules as the tab: no pronouns for the teacher, never names Dasha. TeacherAID
**missed the UW-Madison submission**; it is on the CV as supplementary material for an interview.
The docx entry was inserted by cloning the Composer Compass paragraphs, so formatting matches
(checked in a Word PDF export, still 3 pages).

**The submitted CV docx had typos** (`ad07b0c` fixes them). The Sept 9 proofread covered the `.md`,
but the `.docx` had been hand-edited in Word and was never compared against it. What went out to
UW-Madison, and what the download served until now: "career side to being a compose", "with
automated publishing feature", "Campaign Tracker: A dynamic", and 8 bullets or notes with no final
period. All fixed; "composer" Max fixed himself in Word first. A full line-by-line diff now leaves
two deliberate differences: the docx header omits "Brooklyn, NY", and it shows Portfolio | LinkedIn
as links rather than URLs.

**The submitted cover letter is clean.** It is not in this repo:
`OneDrive\Desktop\Resume and Cover Letters\RISE-AI Assistant Professor Cover Letter.docx` (saved
3:30 PM Sept 9) matches `Academic Cover Letter - UW Madison.md` word for word. An older draft sits in
`OneDrive\Documents` (3:02 PM) with superseded wording and no typos.

**Rule that came out of this:** proofread the exact file that gets sent, and diff it against any
source copy. `build_resume.py`-style edits to a docx go through python-docx on the `w:t` nodes, and
the docx is checked by extracting its text, never by reading the `.md`.

**Open:** Max has not called the TeacherAID CV copy.

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
- Max still owes the copy for the TeacherAID tab's three benefit cards and heading.
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
- ~~Horizontal overflow at 390px, caused by the hero `H1` reaching 426px.~~ Gone since
  2026-09-14: the hero was slimmed and the page is exactly 390px wide at 390.
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

Targeting on the AI track (updated 2026-09-14): AI tool and workflow builder roles, including AI automation, internal tools, low-code, solutions and forward deployed, and automation-focused GTM engineering. Remote, or Madison hybrid. Not "vibe coder" framing. Send `career/base/ai-roles/Maxwell Perkins CV - AI Roles.pdf` with a company-specific copy of `career/base/ai-roles/cover-letter-base.md`.

**🛑 One version of every application file, always current (Max's hard rule, 2026-09-16).** Max once
sent a resume with typos because two copies existed. This can never happen again:
- Each `career/applications/<app>/` folder holds exactly one `.docx` and one `.pdf` per document, and
  they are the latest version. Never leave a backup, "old" or draft copy anywhere, in `career/` or in
  `Documents`, `Downloads` or the Desktop. Scratch copies get deleted the same session.
- Build only with `python career/build.py <app> -m "what changed"`. It exports the PDF, logs
  `versions.md` and runs the check. When Max edits in Word, copy the edits into the source right away.
- **Run `python career/build.py check --all` at the end of every career session and report the
  result.** Any FAIL is fixed before the session ends.
- After Max submits, run `python career/build.py sent <app>`. It freezes the PDFs read-only in `sent/`.
- Details are in `career/README.md` under "The one-version rule".

**Hudson Table over music work (Max's rule, 2026-09-16):** when a posting doesn't involve music, and
especially for event jobs, a resume uses Event Host, Hudson Table (2021-2023) in place of the teaching
and studio entries. Wording and sources are in `career/README.md`. Applied to the WFAA, Savanna and
River Alliance resumes.

The Sprout Suite (CRM + Grant Assistant + Social Manager + Campaign Tracker) is the portfolio centerpiece — four interconnected tools for one real nonprofit, one Supabase backend, actively used in production. Frame as a system, not a list.

The MCP server and The Composer Compass training protocol are the strongest technical differentiators for AI dev roles specifically. The MCP server shows Claude API tool use with real data. The training protocol shows rubric design, structured evaluation, and agent architecture thinking — not just "I called the API."

The Workflow tab is the section most worth investing in. The current copy is solid. The Loom is the weak link — it needs to show intentional methodology, not blind Claude use.

The Composer Compass has grown beyond a portfolio project: it is now also the centerpiece of the academic track's application materials, framed there as an independent research/evaluation project rather than a dev-portfolio tool.
