# AGENTS.md — Bootstrap Instructions

*This file tells an AI agent how to set up the "Product Work AI Kit" system for a user. Any agent that reads project instruction files (Claude Code, Cursor, Codex, Copilot, and others) can act on it. If you are that agent, read this top to bottom, then do the **Setup** steps.*

## Prime directive (read first, obey always)

**The vault is the single source of truth. Anchor to it every session.**

- **Start here.** At the beginning of every session, read `index.md`, then the relevant `work/<project>/context.md`, *before* doing anything else. Arrive oriented.
- **Write everything back into the vault, routed by type.** Nothing important lives only in this chat. If it isn't in the vault, it didn't happen.
- **Never mess up the structure.** No loose files at folder roots, no duplicate context docs, no decision without its *why*. Unrouted, unstructured writes are the one failure mode that breaks this system.
- **Don't invent.** If information is missing, ask the user — don't guess, and don't leave the structure half-built.

Full operating rules for humans + agents: see [`USAGE.md`](USAGE.md).

## What you are building

A Markdown knowledge base ("the vault") plus a set of repeatable workflows that carry a product from a first brief to a developer handoff. The user is a product lead / PM / PO / tech lead. Your job is to make the system remember project state so the user doesn't have to.

## The structure to create

```
<vault>/
├── index.md                     # the map — you read this first every session
├── work/
│   ├── context.md               # every project at a glance
│   └── <project>/
│       ├── context.md           # living state: sprint goal, open threads, blockers
│       ├── decisions/           # one dated file per decision (what + WHY)
│       ├── meetings/            # client syncs + standups
│       ├── proposals/           # PRDs + client proposals
│       ├── notes/               # research, analysis, client-feedback breakdowns
│       └── handoffs/            # dev-ready specs with acceptance criteria
├── knowledge/                   # reusable patterns that outlive one project
└── inbox/                       # raw capture — sort within the week
```

Copy `templates/` and `prompts/` from this repo into the vault (or keep them alongside). Use `example-vault/` as the reference layout.

## Setup

1. **Ask the user** for: their vault location, their current active project name, and which AI tool they primarily use.
2. **Scaffold** the folder structure above at the vault location. Create `index.md` as an entry map, and a `work/<project>/context.md` for their active project using `templates/context.md`.
3. **Install the templates and prompts** so they're easy to reach.
4. **Explain** the pipeline in one paragraph and offer to run the first stage (discovery) on a real brief.

## Operating rules (follow these every session)

- **Read `index.md` first**, then the relevant `work/<project>/context.md`, before doing project work. Arrive oriented; don't ask the user to re-explain the project.
- **Route every artifact by type** using the template that matches (PRD → `proposals/`, decision → `decisions/`, meeting → `meetings/`, dev spec → `handoffs/`).
- **When the user makes a decision, write a decision file** — Context / Decision / Consequences. Capture the *why*, not just the *what*.
- **Keep `context.md` living** — update it in place with current state; don't spawn `context-v2`.
- **Link related notes** so the knowledge base is a graph, not a pile. Use the tool's linking syntax (e.g. `[[note-name]]` wikilinks in Obsidian, or relative Markdown links).
- **After a meeting or client feedback**, produce a note with Summary / Decisions / Action Items (each action has an owner), then extract the actionables into a handoff.

## The pipeline (what each stage produces)

| Stage | Input | Output | Prompt |
|-------|-------|--------|--------|
| Discovery | Brief | PRD (`templates/prd.md`) | `prompts/discovery.md` |
| Proposal | PRD | Client proposal (`templates/proposal.md`) — **scope locks here** | `prompts/proposal.md` |
| Estimation | Locked proposal | Estimate (`templates/estimate.md`) | `prompts/estimation.md` |
| Handoff | Locked scope | Dev spec (`templates/handoff.md`) | `prompts/handoff.md` |

Plus two everyday loops: `prompts/feedback-to-actionables.md` and `prompts/validate.md`.

## Done looks like

The user can drop a brief in and walk it to a handoff without rewriting boilerplate; every decision and meeting is a findable file; and you (the agent) can answer "what did we decide about X?" from the vault instead of asking.
