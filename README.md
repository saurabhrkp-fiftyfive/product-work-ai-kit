# Product Work AI Kit

A tool-agnostic starter kit for running product-lead work through an AI agent + a Markdown knowledge base — from a first client brief all the way to a developer-ready handoff, with nothing lost in between.

Hand this repo to any capable AI agent (Claude Code, Cursor, Copilot, ChatGPT, Gemini) and say *"set this system up for me."* The agent reads [`AGENTS.md`](AGENTS.md), scaffolds the structure, and you start running projects through it.

> **The idea in one line:** the same four artifacts drive every project — PRD, proposal, estimate, handoff. Stop rewriting them from scratch, and stop losing context between a meeting and a build. Turn the repeatable thinking into a **pipeline**, keep everything in a **memory** layer, and close the loop from **meetings to action**.

## The three pillars

1. **Pipeline** — repeatable artifacts, each feeding the next: `Brief → PRD → Proposal → Estimate → Handoff`.
2. **Memory** — one linked, git-tracked knowledge base your agent reads and you can query.
3. **Capture** — meetings and client feedback become notes become shared, tracked action items.

## What's in here

| Path | What it is |
|------|-----------|
| [`starter-kit.md`](starter-kit.md) | The full guide — pillars, the pipeline, the two everyday loops, how to bootstrap. Read this first. |
| [`USAGE.md`](USAGE.md) | **Operating rules** — how you and your agent keep the vault the source of truth so the structure never rots. Read before you start. |
| [`AGENTS.md`](AGENTS.md) | The instruction file your AI agent ingests to set the system up for you. |
| [`templates/`](templates/) | Fill-in Markdown templates: PRD, proposal, estimate, handoff, meeting note, decision, project context. |
| [`prompts/`](prompts/) | Copy-paste prompt templates for each pipeline stage + the feedback and validation loops. |
| [`example-vault/`](example-vault/) | A worked folder layout you can copy as your starting structure. |
| [`bonus-my-ai-stack.md`](bonus-my-ai-stack.md) | Bonus — the tools I use and why, plus notes on custom systems I've built. A menu to borrow from. |

## Quickstart (ship ugly v1)

You do **not** need custom tooling. Minimum viable system:

```bash
# 1. Clone
git clone https://github.com/saurabhrkp-fiftyfive/product-work-ai-kit.git
cd product-work-ai-kit

# 2. Copy the example structure as your own knowledge base
cp -r example-vault ~/my-vault

# 3. Point your AI agent at AGENTS.md and let it scaffold the rest
```

Then run one real project through the pipeline using the [`prompts/`](prompts/), feed the outputs back into your project's `context.md`, and after 2–3 projects you'll have benchmarks, linked decisions, and a memory your agent navigates for you.

## Ground rules (read before you start)

This kit only works if the vault stays the **single source of truth** and your agent **starts from it every session**. Skip that discipline and the structure rots into an unstructured pile — and the AI's output rots with it. The full do/don't list is in [`USAGE.md`](USAGE.md); the one step you must not skip is pinning your agent to the vault.

**Paste this into your agent's standing instructions** (`CLAUDE.md`, `.cursorrules`, `AGENTS.md`, a system prompt):

```
This project's knowledge base ("the vault") is at <PATH-TO-YOUR-VAULT>.
It is the SINGLE SOURCE OF TRUTH.
1. Every session, read `index.md` then the relevant work/<project>/context.md before doing anything.
2. Route every artifact by type (PRD→proposals/, decision→decisions/, meeting→meetings/, dev spec→handoffs/). Never write files loose.
3. When I decide something, write a decision file (Context/Decision/Consequences — capture the why).
4. Keep context.md living — update in place, never duplicate.
5. Link related notes. If information is missing, ask me — don't invent it.
```

## The two everyday loops

**Client feedback → developer actionables:** capture raw feedback → analyze with the team (cluster into themes, split must-fix vs nice-to-have) → extract actionables (task + owner + acceptance criteria) → hand off to devs, linked back to the source → track in `context.md`. A one-hour feedback call becomes a linked chain, not three recollections.

**Generate with one agent, validate with another:** hand a code change, proposal, or estimate to a *second* AI agent for an independent review pass — fresh eyes that don't share the first agent's assumptions. Capture the verdict as a note. Generate → validate → document.

## Why it works

Your memory stops being the database. Decisions carry their *why*. Onboarding becomes a link instead of a two-week download from someone's head. And the AI arrives already oriented, because it reads the knowledge base at the start of every session.

The tool matters less than the three habits: **repeatable artifacts, persistent linked memory, meetings that end in action.**

## License

[MIT](LICENSE) — use it, fork it, adapt it to your stack.
