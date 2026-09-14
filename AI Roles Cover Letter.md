# Cover Letter: AI Tool and Workflow Roles (base draft)

Swap in the bracketed company paragraph for each posting. Everything else stays.

---

Dear [Hiring Manager / Company] Team,

Three years ago, AI went from a curiosity to the thing I think about most. As a composer, I wanted to know what it could really do for someone who already knows how to make music. A year of evaluating AI models on music at Handshake AI showed me where they fail, and convinced me the fear of AI replacing creative work is more science fiction than reality. Now I want to build AI tools as my career.

My most ambitious project is The Composer Hub. At its center is The Composer Compass, which does not compose music; it learns a composer's process and helps them think it through. Behind a simple interface, an analysis agent works from a structured intake, MCP tools that read the score, and retrieval over the composer's own work. Around it I built a career CRM and a virtual agency of Claude Code agents.

What I am proudest of is how I trained it. I wrote a scoring rubric, ran controlled experiments that changed one variable at a time, compared models side by side, and worked through sixteen versions of the system prompt. One good answer was never the goal. I needed the agent to be useful every time, so I ran pieces through independent sessions and checked whether the conclusions held. On my piano sonata, two separate runs reached the same structural decisions. When the agent kept making the same kind of error, I moved the fix into the data layer instead of prompting around it. I have tested it on my last three pieces.

The same skills run in production. The Sprout Suite is four tools on one backend that a Brooklyn nonprofit's team uses every day, including an MCP server that gives Claude live CRM data. TeacherAID runs a working music teacher's scheduling, pay, and booking, with Claude's observations in its scheduled pay-period summaries.

[Company paragraph, 2 to 3 sentences: name what the posting asks you to build, in its own words, and point to the thing you have already shipped that matches it.]

I would love to bring that same approach to [Company]. My portfolio, with live demos of each tool, is at ai-portfolio-landing-page.vercel.app.

Thank you for your time and consideration,

Maxwell Perkins
maxwellhperkins@gmail.com | 925-259-1748

---

## NOTES (not part of the letter)

**Length.** About 340 words before the company paragraph, so about 390 with it. The master doc's
target for this track is 250. If a posting calls for short, cut in this order: the "Around it I
built" sentence, then "I have tested it on my last three pieces", then the Handshake clause about
science fiction.

**What is kept from the UW letter:** the curiosity opening, the science fiction line, "does not
compose music; it learns your process", MCP and retrieval, and the three pieces. **What is cut:**
the curriculum paragraph, the ethics paragraph, and the RISE-AI close.

**Every claim, with its evidence** (composers-compass paths, checked Sept 14, 2026):

| Claim | Evidence |
|---|---|
| A year at Handshake AI | Max, Sept 14 (the UW letter's "two years" was wrong for this CV) |
| MCP tools that read the score | `mcp/composer-assistant-server/server.py`: `analyze_score`, `check_voice_leading` (music21) |
| Retrieval over the composer's own work | ChromaDB `score_sidecars` collection. **Not** a theory library: it holds no books (`docs/deliveries/2026-09-09/README.md:39-42`) |
| Scoring rubric | Rubric v1.0 (five dimensions, two modifiers, scored runs) and v2.0 |
| One variable at a time | `training/experiment-sop-v1.4.md:14` |
| Compared models side by side | Julie's Suite v1: Sonnet, Haiku and Opus, each with thinking on and off. Both Haiku runs described the wrong piece; Sonnet with thinking scored 20/20 |
| Sixteen system prompt versions | v1.0 through v5.9, `training/CHANGELOG.md:1199-1307` |
| Two separate runs, same structural decisions | Piano sonata constitution comparison: "Every major structural decision ... is consistent across both runs, despite the runs being independent sessions" |
| Fix moved to the data layer | Counting errors appeared in every run; fixed at the data layer in Session 86. No run after the fix is recorded, so the letter claims the fix, not a result |
| Tested on my last three pieces | Chaconne (bass fugue), Piano Sonata No. 1, Julie's Suite |

**Do not write, if asked to add results:**
- "Used it to write my last three pieces." Only the bass fugue was written with the protocol. The
  sonata was analyzed when finished; Julie's Suite used a plain Claude chat.
- "Statistically reliable", "blind-scored", or anything about variance. There are no repeated
  identical runs and no blind judging. The reliability claim rests on independent runs agreeing.
- A theory library or books in the retrieval pipeline.

**Interview-ready detail** (true, too long for the letter): the Haiku runs described the wrong
piece; v4.2 of the prompt failed outright and v5.1 was the first excellent result; the thinking-on
and thinking-off runs turned out to differ in kind rather than quality, which led to a design that
runs both and merges by section; Max graded one guide "Correctly identified a problem I actually
have."

**Example company paragraph** (AARP, Engineer I, AI Agents):
> AARP is looking for someone to build agents that return structured, schema-valid output and work
> from retrieved context. That is the pattern behind my research protocols, which return
> schema-validated JSON the Sprout CRM imports directly. Building agents for an organization that
> serves millions of people is exactly the work I want to do.
