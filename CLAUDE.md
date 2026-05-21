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
| [index.html](index.html) | Main portfolio page — all projects, methodology, contact |
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
- **One file per page.** index.html and resume.html are self-contained. Do not split into partials or components.

---

## Deployment

Push to main. Vercel picks it up automatically. No build command, no output directory to configure — Vercel serves the files directly.

To test locally: open `index.html` in a browser, or run `npx serve .` if you need a local server for relative path testing.

---

## Portfolio Structure (index.html)

The page has tabbed sections:

| Tab | Content |
|---|---|
| In Use | Live production tools — Sprout Suite (CRM, Grant Manager, Social Manager), QR Tracker |
| Building | Projects in active development |
| Experiments | Music AI and other research work |
| Workflow | "How I Work with Claude" methodology section |

Each project card has: title, status tag (Live / MVP / WIP), tech tags, description, screenshot or Loom placeholder, and links.

---

## Status Tags

```
.status-live    green    — deployed and actively used in production
.status-mvp     yellow   — functional but not in active production use
.status-wip     purple   — actively being built
```

---

## Known Updates Needed

These are tracked in `career-search-master.md` and should be addressed before the next round of applications:

1. **Headline** — "Vibe Coder" is the current title. Consider leading with output-focused language instead. "Vibe coder" can stay in the methodology section where it's earned context.
2. **About Me section** — missing. One paragraph: who Max is, why Sprout Society specifically, what drives the work.
3. **"In production" language** — none of the project descriptions explicitly say these tools are used by a real nonprofit. Add it.
4. **Social Manager** — listed as "in-progress" but V2 is functional. Update status tag and description.
5. **Development process detail** — project descriptions are thin. Add problem-to-solution framing for 2-3 projects. Example: "V1 used localStorage. V2 rebuilt with Supabase, a human-in-the-loop approval pipeline, and Instagram publishing via Composio."

---

## Career Context

Targeting: vibe coding / low-code development roles, junior AI development positions.

The Sprout Suite (CRM + Grant Manager + Social Manager) is the strongest story — three interconnected tools built for one real organization. Frame it as a system, not three separate projects.

For AI dev roles: the Claude API integration in the Grant Manager (tool use, structured JSON output, research protocol prompting) is the differentiator. Highlight it explicitly.
