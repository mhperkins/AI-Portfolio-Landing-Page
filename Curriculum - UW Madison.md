# Certificate in AI-Assisted Music Practice

**Sample Curriculum. Draft for review.**

Prepared by Max Perkins for the Assistant Professor of Music Technology and Artificial Intelligence position (RISE-AI), Mead Witter School of Music, UW-Madison.

4 courses · 12 credits · undergraduate, no coding background required · 15-week semester format

---

## Teaching Philosophy

I don't teach students to make AI compose music. Generation is the least interesting, least durable thing AI does for a trained musician.

I've spent the last several months building AI tools for real use, not classroom demos: a composition-assistance tool that analyzes a composer's own sketches and surfaces unexplored paths in their own material; a CRM and outreach system now running a nonprofit's daily operations; a public QR-tracking tool I use for both concert marketing and organizational work. The clearest lesson from that work is that the skill worth teaching isn't prompting tricks. It's specification, evaluation, and judgment, the same disciplines a trained musician already practices, redirected at a new instrument.

That distinction had to be engineered, not just intended. Early in the composition tool's development, its guidance language read as directives, actionable suggestions a composer could simply follow. I rewrote the system prompt so every suggestion became an *investigative path* instead: a place to look, never a decision made for you. When the model kept quietly slipping back into prescriptive habits no matter how the prompt was worded, the fix wasn't a better sentence. It was removing the data the model was leaning on. Ethical AI use in a creative field is a design constraint you build and re-enforce, not a value you state once.

**Undergraduate music majors are already trained for this work, they just don't know it yet.** Critical listening is rubric design. A rehearsal log is a session log. Economy of gesture in orchestration is the same discipline as scoping an AI task to the effort it actually deserves, no more, no less. This certificate makes that transfer explicit.

The foundations course asks something specific of a non-technical student: not to learn to code, but to learn to *read* what's being built well enough to direct it. That means basic interface literacy sits alongside prompting and evaluation from week one, hierarchy, affordance, feedback, consistency, the vocabulary that lets a music major give a technical collaborator useful direction on something they didn't build themselves.

> **Grounding note:** the arc this curriculum teaches, manual memoryless prompting → structured specification → rubric-based evaluation → codified, cost-aware practice, is the real arc of my own development across five-plus tools over roughly five months, compressed here into a semester and aimed at a student's own music practice instead of mine.

---

## Certificate at a Glance

| | |
|---|---|
| Total credits | 12 |
| Sequence | 101 → 210 + 310 → 410 |
| Audience | Music majors |
| Capstone deliverable | Assistive tool |

### AIM 101 — Intro to AI & Vibe Coding: Foundations of Human-AI Collaboration
3 credits · full syllabus below

Specification, memory, evaluation, and cost-conscious judgment, plus enough interface literacy to direct technical work you don't build yourself. No prior technical background. Prerequisite for the rest of the certificate.

### AIM 210 — Music Technology and AI
3 credits · sketch, content lead

The 101 skills applied to real music tasks: score and sketch analysis, arranging aid, production and marketing tooling, using case studies from working assistive tools.

### AIM 310 — AI Ethics and Sustainability in Music
3 credits · sketch, content lead

Authorship and ownership, labor and livelihood, environmental and computational cost, and guardrail design as a craft, extending the Week 14 exercise from 101 into a full course.

### AIM 410 — Capstone in AI-Assisted Music Practice
3 credits · sketch, content lead

Design, specify, and document an original assistive AI tool or process for a real music task. Non-generative by design: the tool augments a musician's own material, it never produces finished music in their place.

---

## AIM 101 — Sample Syllabus

### Learning Objectives

1. Direct an AI collaborator through clear, structured specification rather than vague requests.
2. Maintain project memory across sessions with a written brief, the AI-work equivalent of a rehearsal log.
3. Read and critique a digital interface using basic UI/UX vocabulary (hierarchy, affordance, feedback, consistency, accessibility) well enough to give useful direction on something you didn't build.
4. Design a rubric to evaluate AI-generated output against a real standard, rather than accepting the first draft.
5. Reason about the cost and effort of an AI-assisted task, and scale your approach to match.
6. Recognize where a tool's design choices carry ethical weight, and build guardrails before they're needed.

### Grading

- Project briefs & process logs: 30%
- Evaluation & critique assignments: 20%
- Weekly exercises & participation: 20%
- Final presentation & reflection portfolio: 30%

### Weekly Schedule

| Wk | Topic | Core idea | Deliverable |
|---|---|---|---|
| 01 | Orientation, AI Is a Context Window, Not a Colleague | Why "vibe coding" still requires discipline | Reflection: your prior AI use, honestly assessed |
| 02 | Brainstorming Through Constraints | Open questions produce noise; constraints produce signal | Rewrite a vague prompt as a constrained one |
| 03 | Structured Writing as Interface | Markdown and templates as reusable "slots" for output | Template a recurring task |
| 04 | Project Memory | A written brief is your rehearsal log for AI work | Draft: first project brief |
| 05 | Workshop, Project Brief I | Peer review against a shared rubric | Revised brief |
| 06 | Reading Interfaces, UI/UX for Non-Technical Creators | Hierarchy, affordance, feedback, consistency, accessibility | Critique three real interfaces |
| 07 | Specifying a Build | You write the spec, the AI writes the code, you review the result | Spec a simple tool using Week 6 vocabulary |
| 08 | How Systems Fit Together | Enough conceptual literacy to specify integrations, no code required | Diagram a tool's moving parts |
| 09 | Training and Evaluation | "It worked once" is not evidence it works | Draft: an evaluation rubric |
| 10 | Workshop, Evaluation Rubric | Test the rubric against real AI output | Revised rubric |
| 11 | Workflows and Automation | Turning a recurring task into a repeatable protocol | Write a one-page protocol |
| 12 | Diagnosing Failure | A good failure report is half the fix | Failure report from a real breakdown |
| 13 | Cost and Effort as Craft | Matching effort to the size of the task | Budget a project across an effort scale |
| 14 | Guardrails by Design | Building a constraint into a tool, not just stating a value | Redesign a system prompt's boundaries |
| 15 | Final Presentations | Present your process portfolio | Final portfolio: brief, rubric, protocol, reflection |

### AI Use Policy

This course is about AI, so its AI-use policy has to be more specific than most. Every assignment states which parts must be your own thinking (the brief, the rubric criteria, the reflection) and which parts an AI collaborator may draft under your direction (first-pass structure, code, sample text). Submitting AI output as your own critical judgment, uncredited, is a violation; directing an AI collaborator and documenting that direction is the point of the course.

### Accessibility

Standard UW-Madison McBurney accommodation language applies. [Insert current university accessibility statement.]

---

## Rest of the Sequence

AIM 210, 310, and 410 are sketched at the level of a course description and learning objectives here, deliberately. The process pedagogy above is domain-general, and the music-specific content in these three courses is where my own compositional and pedagogical judgment, not my development history, should lead.

**AIM 210 — Music Technology and AI**
Case-study driven: students apply 101's specification and evaluation skills to score/sketch analysis, arranging assistance, notation and production workflows, and small-scale marketing/logistics tooling. Every case study is an assistive tool, never a generator.

**AIM 310 — AI Ethics and Sustainability in Music**
Authorship and training-data provenance, labor displacement and musicians' livelihoods, the environmental cost of compute, and cultural questions in AI-generated music, taught through guardrail-design exercises rather than lecture alone.

**AIM 410 — Capstone in AI-Assisted Music Practice**
Students specify, direct the build of, and document an original assistive tool for a real task in their own practice. Deliverable is the tool plus the same process portfolio format from 101: brief, rubric, protocol, reflection.

---

*Draft prepared for internal review, not a UW-Madison catalog document. Course numbers, credit totals, and policy language are placeholders pending institutional review.*

*Live formatted version: https://claude.ai/code/artifact/b4355685-0c47-4aa3-aa7d-45fbe3451fae*
