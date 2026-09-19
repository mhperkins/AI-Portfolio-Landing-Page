# Slideshow tutorial checklist

Goal (Max, 2026-09-18): every slideshow on the portfolio site works like the Career Desk one, as an
interactive tutorial that can open full screen. Tick a box when it is true on disk, and add the commit.
Status as of 2026-09-18.

## Done means (the Career Desk standard)

A slideshow is done when all of these hold. The reference is `demo/career-desk-demo.html` on the page's
Career Desk tab (commits `c094867` and `aebf85b`).

- [ ] **One step at a time:** the slide dims under a veil, and one highlighted part shows with its
      numbered blurb open as a popup beside it
- [ ] **Next and Back** step within a slide; a slide's last step moves to the next slide, and its first step
      goes back to the previous slide's last step
- [ ] **Start over** on the final step returns to step 1
- [ ] **Steps are numbered across the whole tool,** not per slide
- [ ] **All the old content kept:** every note became a popup, word for word, plus a short popup title
- [ ] **Full screen:** a Start button over the preview opens the tutorial at nearly full window size, at
      step 1; Close, Esc, or a click on the backdrop returns to the same spot on the page
- [ ] **Phones (under 760px)** skip the Start button and run inline, with the popup pinned to the bottom of
      the screen
- [ ] **Popups never cover their own highlight,** and none is clipped (a popup that must sit above its
      node floats over the page instead of moving the nodes; see Compass step 9)
- [ ] **Verified headless** at 1280, 960, and 390 with touch: every step reachable forward and back, zero
      script errors, no sideways scroll on a phone, and zero em dashes

## The slideshows

| # | Slideshow | Tab | Standalone tutorial | Steps | Full screen | On the site |
|---|---|---|---|---|---|---|
| 1 | Career Desk | Career Desk | `demo/career-desk-demo.html` | 12 | Yes | **Yes** (`aebf85b`) |
| 2 | Composer Compass | Composer Hub | `demo/compass-tutorial-demo.html` | 13 | Yes | No |
| 3 | Composer CRM | Composer Hub | `demo/crm-tour-demo.html` (another session, in progress) | 18 | Yes | No |
| 4 | Virtual Agency | Composer Hub | none; built straight on the page (source `demo/agency-demo.html`) | 12 | Yes | Committed (`5c40aed`) |
| 5 | TeacherAID | TeacherAID | none; built straight on the page (source `demo/dasha-demo.html`) | 18 | Yes | Committed (`5c40aed`) |
| 6 | Sprout CRM | Sprout Suite | `demo/sprout-crm-tour-demo.html` | 20 | Yes | Committed, not pushed |
| 7 | Grant Finder | Sprout Suite | not started (source `demo/grant-demo.html`) | 17 | No | No |
| 8 | Social Planner | Sprout Suite | not started (source `demo/social-demo.html`) | 15 | No | No |
| 9 | Campaign Tracker | Sprout Suite | not started (source `demo/campaign-demo.html`) | 10 | No | No |

Step counts for rows 4 to 9 are the notes in each standalone; each note becomes one step.

## Per slideshow

- [ ] **1. Career Desk:** Back across slides is now in the shared `initTour()` on the page (2026-09-18, with
      the Sprout CRM transplant), so Career Desk, Agency, TeacherAID and Sprout CRM all have it. Left: the
      standalone `demo/career-desk-demo.html` still lacks it. Also found at 960 wide, already on the
      live site: Career Desk step 1's popup runs 3px past the overlay's bottom, and TeacherAID step 6's
      popup covers its highlight
- [ ] **2. Composer Compass:** standalone done and verified (306 checks). Left: transplant into `index.html`
      over the current Compass panel, then verify on the page
- [ ] **3. Composer CRM:** standalone built by a parallel session. Left: that session finishes it, then
      transplant
- [ ] **4. Virtual Agency:** on `index.html` through the shared `initTour(root, 'ag')`, built by a parallel
      session and not committed yet. Left: commit it, and add Back across slides to `initTour()` (item 1)
- [ ] **5. TeacherAID:** on `index.html` through `initTour(root, 'ta')`, verified by that session, not committed
      yet. Left: commit it, and Back across slides (item 1)
- [ ] **6. Sprout CRM:** standalone done and verified 2026-09-18 (903 checks at 1280 and 960 full screen,
      and 390 with touch; screenshots checked by eye). Prefix `sc-`, so on the page it runs as
      `initTour(root, 'sc')` once `initTour()` gains Back across slides. Popup titles are Claude's drafts.
      Transplanted 2026-09-18 over the Sprout CRM panel; page verified at 1280, 960 and 390 (every step
      forward and back, Start over, Esc, `#crm`, the other Sprout carousels). Left: Max's look, push
- [ ] **7. Grant Finder:** build, then transplant. Pipeline pins 2 to 4 highlight whole columns through
      `.demo-col` overlays, so a column must be able to be the highlight
- [ ] **8. Social Planner:** build, then transplant
- [ ] **9. Campaign Tracker:** build, then transplant

Also decide: does `teaching.html` (branch `teaching-page`, not live) get the same treatment before it merges?

## How to build one (the order that worked)

1. Copy the source standalone to `demo/<name>-tour-demo.html`. The source stays untouched.
2. By script, turn every pin into a highlight (`data-hl`) and every note into its popup (`data-for`),
   numbered across the tool. Add a short title per popup.
3. Copy the step script and the full-screen block from `compass-tutorial-demo.html` or
   `career-desk-demo.html`, then set each popup's side (`data-at`: right, left, below, below-end, above,
   above-start) so no popup covers its highlight.
4. Verify headless (see "Done means"), then show Max.
5. Transplant into `index.html` (see the rules below).

## Rules while sessions run in parallel

- **Build in `demo/` freely:** each standalone belongs to one session, so they cannot collide.
- **`index.html` is shared by every slideshow.** Only one session transplants at a time, on its own branch
  in a git worktree, merged into `main` after the other sessions have committed. The shared carousel
  script (`initDemoPops()`, `measureTabBar()`, and the `[data-demo-panel]` initializer) is where
  transplants collide.
- **Before committing, run `git status` and stage named files only, never `-A`.** Twice before, a commit
  swept up another session's uncommitted `index.html` work (`f81c79a`, `0b73ae2`).
- **Update this checklist rather than `CLAUDE.md` mid-session;** fold it into `CLAUDE.md` at the end.
- Nothing goes live until Max says push.
