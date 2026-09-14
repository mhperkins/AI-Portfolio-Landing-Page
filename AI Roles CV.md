# Maxwell Perkins
Brooklyn, NY (relocating to Madison, WI) | maxwellhperkins@gmail.com | 925-259-1748
Portfolio: ai-portfolio-landing-page.vercel.app | LinkedIn: linkedin.com/in/maxwell-perkins-702a82207 | GitHub: github.com/mhperkins

---

## SUMMARY

AI tool and workflow builder. Ships production internal tools on Next.js and Supabase, Claude API and MCP integrations, and structured prompts that return data an app can import directly. Background in LLM evaluation, nonprofit operations, and music.

---

## SKILLS

**AI:** Claude API, Claude Code, MCP servers, prompt and rubric design, LLM evaluation, structured JSON output, RAG (ChromaDB)
**Automation:** n8n, scheduled jobs (pg_cron, Vercel cron), REST APIs, Instagram API (via Composio), Python scripting
**Web and data:** Next.js, React, JavaScript, TypeScript, Tailwind CSS, Supabase (PostgreSQL, Auth, RLS), SQL, Vercel, Git

---

## APPLIED SYSTEMS

**The Sprout Suite** | 2025-Present
*Four production tools for a Brooklyn nonprofit on one Supabase backend, replacing paid software.*
- **MCP server:** exposes the live CRM to Claude as 14 tools (relationship health, search, touchpoint logging, dedupe).
- **Research protocols:** multi-phase prompts that return schema-validated JSON the CRM and Grant Tool import directly.
- **Social Media Manager:** posts move from draft to approved to scheduled, then publish to Instagram with human sign-off.
- **Grant Tool:** tracks each grant from research brief to submission, with versioned answer drafts, tasks, and export.
- **Campaign Tracker:** QR codes that can be retargeted after printing, with scan counts on Vercel and Supabase.
- **Weekly digest:** built an n8n workflow that pulled data from all four tools and added a Claude analysis layer.

**TeacherAID** | 2026-Present
*Scheduling, payroll, and booking for an independent music teacher, in production on Next.js, Supabase, and Vercel.*
- Logs each lesson in one tap; hours, pay sheets, and student records all update from that entry.
- Sends scheduled email summaries through pg_cron and secured API routes, with Claude observations on each pay period.
- Lets families book open lesson times from a single link.

---

## AI PROJECTS: THE COMPOSER HUB

*AI tools that assist trained musicians in their process instead of generating music for them.*

**The Composer Compass** | 2026-Present
- Analysis agent that works from a structured intake, MCP score tools, and retrieval over the composer's scores.
- Trained with controlled A/B runs, a scoring rubric, and 16 prompt versions across Sonnet, Opus, and Haiku.
- Maps the workflow from planning through sketching, drafts, and engraving in a Next.js canvas built on the Anthropic API.

**Composer CRM** | 2026-Present
- Tracks performers, ensembles, venues, and concerts, with a newsletter builder and AI prospect research.

**Virtual Agency** | 2026-Present
- Claude Code agents, each a system prompt plus tools, that have produced a landing page, program notes, and a campaign.

---

## PROFESSIONAL EXPERIENCE

**Community Manager, Sprout Society** | Brooklyn, NY | February 2026-Present
- Run operations for a three-person nonprofit: membership, 10 to 15 events a month, outreach, social media, and grants.
- Scoped, built, and maintain the organization's internal tools (see Applied Systems).

**Freelance Prompt Engineer, Handshake AI** | Aug 2025-Present
- Annotate AI-generated music; write prompts and rubrics that expose failures in AI musical analysis.

**Founder, Music Major Records LLC** | Jul 2023-Aug 2025
- Owned strategy, product, marketing, and finances for a platform for college musicians, then placed it on hold.

**Private Music Instructor** | 2011-Present
- Piano, drums, audio production, and composition, one-on-one and in groups, with original curricula.

**Producer & Recording Engineer, Misfits' Instruments Studio** | 2018-Present

---

## EDUCATION

**M.M., Music Theory and Composition (Songwriting Concentration)** | New York University, 2022
**B.A., Music Composition, Minor in Business** | University of Wisconsin-Madison, 2014

---

## NOTES (not in the exported files)

- Built from `Academic CV - UW Madison.docx` (same styles, entry lines, italic notes, bullets) by
  `python build_ai_cv.py`, then exported to PDF through Word. Outputs
  `Maxwell Perkins CV - AI Roles.docx` and `.pdf`. The UW-submitted CV is not changed. When Word has
  the CV open (it locks the file), the script falls back to
  `Maxwell Perkins Resume - Community Engagement.docx`, which was built from the same template.
- One page: 10pt body, single line spacing, 42pt side margins.
- Section order is flipped for industry roles: Summary and Skills first, then the shipped systems,
  then the Composer Hub, then experience, with Education last. Teaching Experience folds into
  Professional Experience.
- Every new technical claim was checked against the source repos on Sept 14, 2026: the CRM MCP
  server (`sprout-crm-next/mcp/server.js`, 14 tools), TeacherAID's pg_cron email jobs and Claude
  observations (`dasha-board/CLAUDE.md`), Virtual Agency running in Claude Code
  (`virtual-agency.md`), and the Instagram approval pipeline (portfolio `CLAUDE.md`).
- **The Compass bullets changed on Sept 14** after a check of the composers-compass training record.
  There is no theory library in the retrieval pipeline (it holds no books; only a `score_sidecars`
  collection exists), and the six-dimension rubric (v2.0) was never numerically scored, so both
  claims came out. The replacements cite what ran: A/B experiments, the rubric, 16 prompt versions,
  and Sonnet, Opus and Haiku. The UW-submitted academic CV still says "theory library".
- **The n8n digest is past tense on purpose.** Nothing in the Sprout repo says it still runs.
- **The Social Media Manager bullet changed.** The academic CV says it "publishes posts automatically
  on a content calendar"; the app publishes from a button on an approved card, so this version
  describes the approval pipeline instead.
- Python is listed as scripting only. The master doc lists it as still being learned.
- PMP is omitted: its status has not been confirmed since May. Add it back if it is still in progress.
- Composer and Songwriter (Independent) is dropped, and the studio job is one line, to hold the page.
- Your LinkedIn headline still reads "Vibe Coder / AI Developer." Fix it before sending.
