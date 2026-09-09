# Career Search & Portfolio — Handoff Notes
**Last updated: September 9, 2026**

## Current Situation

The search now runs three parallel tracks. **Arts/nonprofit operations
(`career-search-ops-track.md`) is the primary, ongoing search** — general arts admin roles,
applied to regularly. **This is the next task**: keep applying to arts admin roles on that track,
a different strategy from the academic one (general ops/admin roles, applied to on an ongoing
basis, portfolio/AI framing case-by-case rather than led with). The other two are narrower:

- **AI/dev track** (`career-search-master.md`) — original track, background/secondary. Portfolio
  fully overhauled — Shipped/Building/Workflow tabs, suite carousel, About page, problem/solution/outcome
  on every tool. MCP server shipped and connected to Claude Desktop. n8n weekly digest live.
- **Arts/nonprofit operations track** (`career-search-ops-track.md`) — **primary track, and the
  immediate next task.** General arts admin roles, applied to on an ongoing basis.
- **Academic music technology & AI track** (`career-search-academic-track.md`) — **an outlier, not
  the main strategy.** UW-Madison Mead Witter School of Music, RISE-AI (JR10004513) application
  **submitted September 9, 2026** (CV, cover letter, teaching statement, built around The Composer
  Compass as the focal creative/research work). Search on this track continues in parallel and
  opportunistically: other RISE-AI-like postings will be applied to under this same framing as they
  turn up. This does not represent a pivot away from the ops/arts-admin search; that remains the
  primary, ongoing effort regardless of how the RISE-AI application lands.

The Composer Compass (Music Composition Assistant) — tool scaffolded, training protocol running,
first experiment scored. Unified Sprout Society Suite app planned (hub with navigation across all 4 tools).

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
- The Composer Compass — AI composition studio. Tool is built (Next.js, direct Anthropic SDK, server-side API route). Training protocol active: structured intake form → analysis agent → rubric-based evaluation across 6 model runs. First scoring session completed May 22, 2026. MCP server architecture planned.

**Workflow tab:**
- Loom needs to be redone — current video makes it look like blind Claude use, not intentional technical development
- Composition agent training protocol is a strong concrete example to add to this section

---

## What Was Just Built (May 22, 2026)

- **The Composer Compass** — Next.js app scaffolded and wired:
  - `components/CompositionHub.jsx` — full UI with Pre-Comp, Lo-Res, Hi-Res, Engraving workflow tabs, Brainstorm, Pieces archive, Network, Discover
  - `app/api/ai/route.js` — server-side Anthropic API proxy (API key secured, `mcp_servers` field passed through for future MCP integration)
  - `app/compass/page.js` — thin route wrapper
  - `CLAUDE.md` written with full project context
- **Training infrastructure** — 5 documents in `training/`:
  - `system-prompt.md` — canonical analysis agent role
  - `intake-form.md` — 8-section intake for new pieces
  - `evaluation-rubric.md` — generalized 5-dimension scoring framework (piece-agnostic)
  - `experiment-sop.md` — repeatable experiment protocol
  - `methodology.md` — five-phase analytical process reference
- **Scoring project set up** in Claude Desktop — separate from the composition project to keep evaluation clean
- **First scoring session completed** — Run 1 (Sonnet EXT) scored 12/12 on machine dimensions (D1, D3, D4 all 4/4). D2 and D5 pending composer scoring.

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
- Direct Anthropic SDK usage — server-side API proxy with model routing and token management (The Composer Compass)
- Human-in-the-loop workflow design
- Zod schema validation
- Structured research protocols functioning as system prompts, producing importable JSON
- Agent evaluation and rubric design — structured multi-run experiment protocol with generalized scoring framework

### The Gap (Still Honest)
Technical depth is growing but most code is still Claude-generated. The improving skills:
- Reading and understanding code without Claude
- Debugging judgment
- Vocabulary to describe what's been built

What still needs building:
- Ability to make small changes independently
- Python basics
- Streaming responses and prompt caching in direct SDK usage

---

## Next Best Steps — Priority Order

### Immediate
- [ ] Complete Wellfound profile and AI interview
- [ ] Complete Contra profile setup
- [ ] Continue applying 3-5 roles per week
- [ ] Score D2 and D5 on Run 1, complete experiment log entry

### Short Term
- [ ] Score Runs 2–6 (one per day, cold evaluation)
- [ ] Record new Loom for Social Media Manager V2
- [ ] Redo Workflow tab Loom — show the composition training protocol as a concrete example of the methodology
- [ ] Update Workflow tab copy in portfolio to include the composition agent training approach
- [ ] Start reading own code daily — one component, explain each function out loud

### Medium Term
- [ ] Build The Composer Compass MCP server (expose system prompt, intake form, rubric as resources; add `log_session` and `get_piece_history` tools)
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
| The Composer Compass | — | Building |

---

## Job Search Strategy Notes

- Lead with the Sprout Suite as a system, not individual projects
- Four interconnected tools for one organization, one backend, actively used in production
- MCP server is the strongest technical differentiator for AI dev roles specifically — shows tool use, resource design, multi-step reasoning with real data
- The Composer Compass training protocol is the second technical differentiator — demonstrates rubric design, structured evaluation, and agent architecture thinking, not just "I called the API"
- Workflow framing needs update — the composition training protocol is the concrete example of intentional methodology that the current Loom doesn't show
- Arc.dev rejection likely a marketplace seniority bar, not a portfolio problem — not the right channel right now
- Academic track (UW-Madison RISE-AI) is a one-off outlier, not a new primary strategy. Ops/arts-admin remains the main ongoing search; keep applying to general arts admin roles regardless of how the RISE-AI application lands
