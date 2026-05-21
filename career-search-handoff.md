# Career Search & Portfolio — Handoff Notes
**Last updated: May 21, 2026**

## Current Situation

- Targeting **vibe coding** and **low-code development** roles, plus junior AI development positions
- Updated resume is now live on the portfolio at [ai-portfolio-landing-page.vercel.app](https://ai-portfolio-landing-page.vercel.app/)
- Self-teaching HTML and JavaScript alongside building projects with Claude
- Social Manager V2 is now functional — portfolio listing not yet updated
- n8n trial active (13-day window) — building a cross-tool weekly digest automation
- MCP server on the CRM is next after n8n — highest portfolio value item for AI dev roles

---

## Portfolio — Current State

**Live at:** https://ai-portfolio-landing-page.vercel.app/

**Projects shown:**
1. Sprout Society CRM — contact tracking, events, Claude-powered profile generation
2. Grant Manager V2 — Claude-assisted research and application drafting, Supabase-native
3. Social Content Planner — listed as "in-progress" but V2 is now functional and deployed
4. QR Scan Tracker — analytics for dynamic QR codes
5. Music Composition Assistant — agent-based tool, in-progress

**Pending portfolio updates (do before next application round):**
- Update Social Manager status from "in-progress" to live V2
- Change headline from "Vibe Coder" to output-focused framing
- Add About Me section
- Add "actively used in production at Sprout Society" language to all three Sprout tools
- Add development process detail to 2-3 project descriptions

**Methodology section:** "How I Work with Claude" — explains structured documentation, Claude Code in VS Code, refined prompting

---

## Key Advice Given

### Positioning
- **"Vibe Coder" as the headline title is a risk.** It resonates with the right companies but gives traditional engineering teams a reason to dismiss the portfolio before seeing the work. Recommendation: lead with the output ("Building AI-powered internal tools") and use "vibe coder" in the methodology section where it's earned context — not as the first thing people read.
- The Sprout suite (CRM + Grant Manager + Social Manager) is a strong story as **a cohesive system built for one real organization in production**. That's not a side project — frame it as such.

### What's Missing
1. **About Me section** — the portfolio answers *what* was built but not *who* and *why*. One paragraph: background, why Sprout Society specifically, what drives the work. Humanizes everything else.
2. **"In production" language** — nowhere does the portfolio say these tools are actively used by a real nonprofit. Say it explicitly.
3. **Development process detail** — add the problem-solution framing to each project. Example: *"V1 had 12+ views and localStorage. Rebuilt to 4 focused views with Supabase, a human-in-the-loop approval pipeline, and Instagram publishing via Composio."*
4. **Social Manager needs updating** — still listed as "in-progress." It's now a fully functional V2 with a live Vercel deployment.

### On the 0 Loom Views
The issue is **before** the portfolio, not the portfolio itself. Loom views require someone to click through from the resume. Fix priority order:
1. Updated resume (already done) — biggest immediate impact
2. Portfolio positioning (About Me, production framing)
3. More targeted applications matched to specific job postings

---

## On Technical Expertise

### What's Already There (undersold)
- OAuth flows (Composio, Canva scaffold)
- Row Level Security in Supabase
- Multi-step API chains (Instagram Graph API: container → poll → publish)
- REST API proxy routes in Next.js
- Real-time auth with Supabase
- Claude API with tool use (grant writer)
- Human-in-the-loop workflow design
- Zod schema validation on all CRM data writes (not just type checking — full runtime validation with safe parse helpers)
- Written research protocols that function as structured system prompts — multi-phase, schema-aware, produce importable JSON. This is prompt architecture, not just prompt use.

### The Honest Gap
All code has been generated via Claude. The skills that exist:
- Product thinking and system design
- API orchestration — knowing which services to connect
- Debugging judgment — reading errors, understanding fixes
- UX and workflow design decisions

What needs building:
- Ability to read and explain the code without Claude
- Ability to make small changes independently
- Vocabulary to describe what's been built in technical terms

### Recommendation
Don't build more tools to compensate. Instead:
1. **Understand what's already built** — go through SocialManager.jsx, explain each function in plain English. Connect product understanding to code logic.
2. **Build one small thing yourself** — a single page (to-do list, form that saves to Supabase). Use Claude to help but type every line. Close the gap between knowing *what* to build and being able to build it.

---

## Next Best Steps — Priority Order

### Immediate (this week)
- [ ] Update portfolio: change Social Manager from "in-progress" to live with V2 screenshots
- [ ] Add "in production at Sprout Society" language to all relevant projects
- [ ] Change headline from "Vibe Coder" to something output-focused

### Short term (2–4 weeks)
- [ ] Add About Me section to portfolio
- [ ] Add development process detail to 2–3 project descriptions (problem → decision → solution)
- [ ] Record a new Loom for the Social Manager V2 showing the full publish pipeline
- [ ] Start learning the code you've built (read through one component per day, explain it out loud)

### This week (time-sensitive — n8n trial)
- [ ] Build n8n weekly digest: one workflow pulling CRM + Grant + Social data, Claude analysis, email output
- [ ] Get at least one complete run delivering before trial ends

### Short term (2-4 weeks)
- [ ] Build MCP server on the CRM (120 lines, `@modelcontextprotocol/sdk`, stdio transport for Claude Desktop)
- [ ] Add About Me section to portfolio
- [ ] Add development process detail to 2-3 project cards
- [ ] Record new Loom for Social Manager V2
- [ ] Read through one component per day — explain each function out loud

### Medium term (1-2 months)
- [ ] Convert n8n workflow to native Vercel cron (no subscription dependency)
- [ ] Connect real Sprout Society Instagram account (get IG_ACCESS_TOKEN)
- [ ] Set up Canva Connect API access for the Canva import feature

### Job Search Strategy
- **Target specific postings** — reverse engineer the requirements and build toward them rather than building generically
- **Lean into the Sprout suite** — three interconnected tools for one organization is a portfolio story, not just a list of projects
- **For AI development roles specifically:** the existing Claude API integration in the grant writer shows tool use. Highlight that explicitly. Consider adding streaming, structured outputs, or a multi-turn agent to demonstrate deeper understanding.

---

## Tools & Repos

| Tool | Repo | Status |
|---|---|---|
| Sprout CRM | github.com/mhperkins/Sprout-CRM-tool-Next.js | Live |
| Grant Manager V2 | github.com/mhperkins/sprout-tools | Live |
| Social Manager V2 (standalone) | github.com/mhperkins/sprout-social-tool | Live — portfolio listing not updated yet |
| Portfolio | github.com/mhperkins/ai-portfolio-landing-page | Live |

## Builds in Progress

| Build | What it is | Status |
|---|---|---|
| n8n weekly digest | Scheduled cross-tool email with Claude analysis | In progress — 13-day trial window |
| CRM MCP server | Claude tools over live CRM data — contacts, health, events, protocols as resources | Planned, starts after n8n |
