# AI System for Product Work — Starter Kit

*A tool-agnostic blueprint you hand to your AI agent (Claude Code, Cursor, Copilot, ChatGPT, Gemini — any of them) to replicate a product-lead workflow: brief → PRD → proposal → estimate → developer handoff, backed by a knowledge base and a meeting-capture loop.*

**How to use this file:** Give it to your agent as context and say *"Set up this system for me. Ask me for the paths and tools you need, then scaffold it."* Adapt names to your stack. Start ugly — a folder of Markdown files and three prompt templates is a working v1.

---

## The idea in one line

The same four artifacts drive every project (PRD, proposal, estimate, handoff). Stop rewriting them from scratch, and stop losing context between a meeting and a build. Turn the repeatable thinking into a **pipeline**, keep everything in a **memory** layer, and close the loop from **meetings to action**.

## The three pillars

1. **Pipeline** — repeatable artifacts, each feeding the next.
2. **Memory** — one knowledge base your agent can read and you can query.
3. **Capture** — meetings become notes become shared action items.

---

## Pillar 1 — The delivery pipeline

Four stages. Each stage's output is the next stage's input. Scope locks with the client *before* hours are estimated — this is the discipline that prevents rework.

```
Brief → [Discovery] → PRD → [Proposal] → Proposal doc → [Estimation] → Estimate → [Handoff] → Dev spec
                        │                     │ (client locks scope here)
                        └── surfaces unknowns before anyone estimates
```

### Stage 1 — Discovery → PRD
Turn a vague brief into a spec. The agent runs a structured interview and **surfaces the unknowns before estimation**.

PRD contains: problem statement · goals · user stories · scope (in/out) · **acceptance criteria** · open questions · dependencies.

> **Prompt template:** "You are a product discovery interviewer. Given this brief: `<brief>`. Ask me one question at a time to fill gaps in a PRD. When you have enough, write a PRD with sections: Problem, Goals, User Stories, Scope (in/out), Acceptance Criteria, Open Questions, Dependencies. Flag anything still unknown."

### Stage 2 — PRD → Proposal
A client-facing document. Epics, scope of work, deliverables, acceptance criteria, prerequisites. **Scope is locked with the client here**, before any hours are calculated.

> **Prompt template:** "From this PRD, write a client-facing proposal: Epics (feature-level only), Scope of Work, Deliverables, Acceptance Criteria, Prerequisites. No hours, no internal notes. Written for a non-technical stakeholder."

### Stage 3 — Proposal → Estimate
Hours from **benchmarks, not guesswork**. Break locked scope into tasks; attach hours from your own historical data; roll up per phase.

> **Prompt template:** "From this locked proposal, produce an estimate: break each epic into tasks, assign hours from these benchmarks `<your past estimates>`, group by phase, total it. Keep delivery phases (QA/UAT/PM) separate from feature work."

*Tip:* your benchmarks improve every project — feed old estimates back in so numbers stay grounded.

### Stage 4 → Developer handoff
A spec the dev team acts on: what to build, what to watch for, and the **acceptance criteria they'll be measured against**.

> **Prompt template:** "Write a developer handoff for this scope: Context, What to Build, Technical Notes / gotchas, Out of Scope, Acceptance Criteria (testable), Definition of Done. Written for an engineer who wasn't in the client calls."

---

## Pillar 2 — The memory layer (knowledge base)

One place holds every project's context, decisions, and research as **linked notes** — structured so your agent can read it and you can ask *"what did we decide about X?"* instead of digging through chat history.

Minimal structure (folders of Markdown — Obsidian, a git repo, anything):

```
knowledge-base/
├── index.md                  # entry point — agent reads this first
├── projects/<project>/
│   ├── context.md            # living project state (update in place)
│   ├── decisions/            # one file per decision (what + why)
│   ├── meetings/             # dated meeting notes
│   └── artifacts/            # PRD, proposal, estimate, handoff
└── knowledge/                # reusable patterns across projects
```

Three habits make it work:
- **Atomic notes** — one idea per file, linked, not one giant doc.
- **Decisions get their own file** — *Context / Decision / Consequences*. Future-you (and the agent) needs the *why*.
- **Context files are living** — update in place; don't spawn `context-v2`.

> **Agent instruction to include:** "At session start, read `index.md`, then the relevant `projects/<project>/context.md`. When I make a decision, write a decision file. When you write any artifact, route it by type and link it back to the project context."

---

## Pillar 3 — Meeting capture loop

A one-hour call becomes a five-line update the team actually reads.

```
Record → Transcribe → Distill → Share
                        │
                        └── Summary · Decisions · Action Items (owner + date)
```

- **Record + transcribe** any tool works (built-in transcription, Whisper, a meeting bot).
- **Distill** to a fixed template so it's scannable: **Summary / Decisions / Action Items** (each action has an owner).
- **Share** the extract, not the transcript. Land the note in the project's `meetings/` folder so it joins the memory layer.

> **Prompt template:** "From this transcript, write a meeting note: Summary (3 lines), Decisions (bulleted), Action Items (owner + due date each), Open Questions. Then give me a 5-line version to paste into team chat."

---

## Two everyday loops the pillars unlock

### Loop A — Client feedback → developer actionables
The product-lead loop that leaks the most value when it lives in someone's head.

**Capture** raw feedback in the project → **analyze with the team** (AI clusters it into themes, flags contradictions, splits must-fix from nice-to-have) → **extract actionables** (task + owner + acceptance criteria) → **hand off** to devs with a note linked back to the source → **track** in `context.md`.

Result: a one-hour feedback call becomes a linked chain — feedback → themes → actionables → handoff → done. One source of truth, not three recollections.

> **Prompt template:** "Here's raw client feedback: `<paste>`. Cluster it into themes. For each: is it must-fix or nice-to-have, does it contradict other feedback, and what's the concrete actionable (task + acceptance criteria)? Then draft a developer handoff for the must-fix items."

### Loop B — Generate with one agent, validate with another
Not all AI work is *generating* — a lot of value is *checking*. Hand a code change, proposal, or estimate to a **second AI agent for an independent review pass** — fresh eyes that don't share the first agent's assumptions. Capture the verdict as a note so the reasoning is documented, not lost in a chat window.

Pattern: **generate → validate → document.** A cheap second-opinion pass that catches problems before they ship and leaves a paper trail either way.

---

## Bootstrap it today (ship ugly v1)

You do **not** need custom tooling to start. Minimum viable system:

1. Make a `knowledge-base/` folder with `index.md` + one `projects/<x>/context.md`.
2. Save the four pipeline prompts + the meeting prompt as reusable templates.
3. Point your agent at the folder as context. Tell it to read `index.md` first.
4. Run one real project through the pipeline. Feed the outputs back into `context.md`.
5. After 2–3 projects you'll have benchmarks, linked decisions, and a memory your agent navigates for you.

The tool matters less than the **three habits**: repeatable artifacts, persistent linked memory, meetings that end in action. Any capable AI agent can run this once it can read your knowledge base.

---

*This is a system, not "AI writes my docs." Consistent structure + persistent memory + AI doing the repetitive lifting = faster proposals, grounded estimates, and nothing lost between a meeting and a handoff.*
