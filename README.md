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
| [`AGENTS.md`](AGENTS.md) | The instruction file your AI agent ingests to set the system up for you. |
| [`templates/`](templates/) | Fill-in Markdown templates: PRD, proposal, estimate, handoff, meeting note, decision, project context. |
| [`prompts/`](prompts/) | Copy-paste prompt templates for each pipeline stage + the feedback and validation loops. |
| [`example-vault/`](example-vault/) | A worked folder layout you can copy as your starting structure. |

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

## The two everyday loops

**Client feedback → developer actionables:** capture raw feedback → analyze with the team (cluster into themes, split must-fix vs nice-to-have) → extract actionables (task + owner + acceptance criteria) → hand off to devs, linked back to the source → track in `context.md`. A one-hour feedback call becomes a linked chain, not three recollections.

**Generate with one agent, validate with another:** hand a code change, proposal, or estimate to a *second* AI agent for an independent review pass — fresh eyes that don't share the first agent's assumptions. Capture the verdict as a note. Generate → validate → document.

## Why it works

Your memory stops being the database. Decisions carry their *why*. Onboarding becomes a link instead of a two-week download from someone's head. And the AI arrives already oriented, because it reads the knowledge base at the start of every session.

The tool matters less than the three habits: **repeatable artifacts, persistent linked memory, meetings that end in action.**

## License

[MIT](LICENSE) — use it, fork it, adapt it to your stack.
