# Career Search & Portfolio — Handoff Notes
**Last updated: May 22, 2026**

## Current Situation

- Targeting AI developer, junior full-stack, and internal tools roles
- Portfolio fully overhauled — Shipped/Building/Workflow tabs, suite carousel, About page, problem/solution/outcome on every tool
- MCP server shipped and connected to Claude Desktop
- n8n weekly digest live, runs every Monday
- Music Composition Assistant agent build starting next
- Unified Sprout Society Suite app planned (hub with navigation across all 4 tools)

---

## Portfolio — Current State

**Live at:** https://ai-portfolio-landing-page.vercel.app/

**Pages:**
- `index.html` — main portfolio with Shipped/Building/Workflow tabs
- `about.html` — standalone About page (linked from nav)
- `resume.html` — PDF resume embed

**Shipped tab — The Sprout Society Suite:**
1. CRM — contact tracking, events, n8n digest, MCP server
2. Grant Assistant — Claude-assisted research and application tracking
3. Social Media Manager — Canva API, Instagram publishing, human-in-the-loop
4. Campaign Tracker — dynamic QR codes, serverless scan tracking via Cloudflare

**Building tab:**
- Music Composition Assistant — agent architecture, rubric-based training, tool use

**Workflow tab:**
- Loom needs to be redone — current video makes it look like blind Claude use, not intentional technical development

---

## What Was Just Built (May 22, 2026)

- Full portfolio overhaul with suite carousel and problem/solution/outcome copy
- CRM MCP server (sprout-crm-next/mcp/server.js) — live on Claude Desktop
- n8n weekly digest automation — live
- About page (about.html) added and in nav on all pages
- Campaign Tracker (formerly QR Scan Tracker) renamed and added to suite
- Social Manager moved from "Building" to "Shipped"

---

## Technical Skills — Updated Assessment

### What's There Now
- MCP server development (Model Context Protocol, stdio transport, tool and resource design)
- n8n workflow automation
- OAuth flows (Composio, Canva)
- Row Level Security in Supabase
- Multi-step API chains (Instagram Graph API)
- REST API proxy routes in Next.js
- Claude API with tool use
- Human-in-the-loop workflow design
- Zod schema validation
- Structured research protocols that function as system prompts, producing importable JSON

### The Gap (Still Honest)
Technical depth is growing but most code is still Claude-generated. The improving skills:
- Reading and understanding code without Claude
- Debugging judgment
- Vocabulary to describe what's been built

What still needs building:
- Ability to make small changes independently
- Python basics
- Direct Anthropic SDK usage (streaming, tool use in code, caching)

---

## Next Best Steps — Priority Order

### Immediate
- [ ] Complete Wellfound profile and AI interview
- [ ] Complete Contra profile setup
- [ ] Continue applying 3-5 roles per week

### Short Term
- [ ] Record new Loom for Social Media Manager V2
- [ ] Redo Workflow tab Loom with a framing that shows technical intentionality
- [ ] Begin Music Composition Assistant agent build (Claude API, tool use, multi-phase architecture)
- [ ] Start reading own code daily — one component, explain each function out loud

### Medium Term
- [ ] Build unified Sprout Society Suite app (hub navigation across all 4 tools, one deployment)
- [ ] Convert n8n workflow to native Vercel cron (no subscription dependency)
- [ ] Connect real Sprout Society Instagram account
- [ ] Learn Python basics

---

## Tools & Repos

| Tool | Repo | Status |
|---|---|---|
| Sprout CRM | github.com/mhperkins/Sprout-CRM-tool-Next.js | Live |
| Grant Manager V2 | github.com/mhperkins/sprout-tools | Live |
| Social Manager V2 | github.com/mhperkins/sprout-social-tool | Live |
| Campaign Tracker | github.com/mhperkins/qr-tracker | Live |
| Portfolio | github.com/mhperkins/ai-portfolio-landing-page | Live |

---

## Job Search Strategy Notes

- Lead with the Sprout Suite as a system, not individual projects
- Four interconnected tools for one organization, one backend, actively used in production
- MCP server is the strongest technical differentiator for AI dev roles specifically — shows tool use, resource design, multi-step reasoning with real data
- Workflow framing needs update — emphasize intentional documentation system and diff review, not just "I use Claude Code"
- Arc.dev rejection likely a marketplace seniority bar, not a portfolio problem — not the right channel right now
