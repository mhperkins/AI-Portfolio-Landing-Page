# AI Tool Portfolio — CLAUDE.md

> Project memory and context for Claude Code. Not committed to git.

---

## What This Is

Max's personal portfolio site. Static HTML — no build step, no bundler, no framework. Push to git and Vercel deploys automatically.

**Live at:** https://ai-portfolio-landing-page.vercel.app

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
| [about.html](about.html) | Standalone About page — linked from nav |
| [resume.html](resume.html) | Resume page — renders the PDF in an iframe with a download button |
| [Software Developer Resume.pdf](Software Developer Resume.pdf) | Current resume, linked from resume.html |
| [images/](images/) | Screenshots and assets |
| [career-search-handoff.md](career-search-handoff.md) | Snapshot of career search status — context for Claude sessions |
| [career-search-master.md](career-search-master.md) | Full ongoing career strategy document |

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
| Building | Composer's Compass — tool scaffolded, agent training protocol active |
| Workflow | How I build tools (CLAUDE.md system, diff review) and how I build agents (intake form, rubric, experiment protocol) |

Each project card has: title, status tag, tech tags, Problem / Approach / Current Phase description.

---

## Status Tags

```
.status-live    green    — deployed and actively used in production
.status-mvp     yellow   — functional but not in active production use
.status-wip     purple   — actively being built
```

---

## Current Portfolio State (May 2026)

All major items from the previous Known Updates list are resolved:
- Headline updated to output-focused language ("I build AI-assisted tools, not prototypes.")
- About page exists (about.html) and About section on index.html
- Problem/solution/outcome framing on all project cards
- Social Manager moved to Shipped tab
- Composer's Compass added to Building tab with full training protocol description
- Workflow tab updated with agent training methodology paragraph

**Remaining:**
- Loom for Social Media Manager V2 needs to be recorded
- Workflow tab Loom needs to be redone to show the composition training protocol

---

## Career Context

Targeting: AI developer, junior full-stack, and internal tools roles. Not "vibe coder" framing.

The Sprout Suite (CRM + Grant Assistant + Social Manager + Campaign Tracker) is the portfolio centerpiece — four interconnected tools for one real nonprofit, one Supabase backend, actively used in production. Frame as a system, not a list.

The MCP server and the Composer's Compass training protocol are the strongest technical differentiators for AI dev roles specifically. The MCP server shows Claude API tool use with real data. The training protocol shows rubric design, structured evaluation, and agent architecture thinking — not just "I called the API."

The Workflow tab is the section most worth investing in. The current copy is solid. The Loom is the weak link — it needs to show intentional methodology, not blind Claude use.
