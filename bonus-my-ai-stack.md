# Bonus — My AI Product Stack (what I use & why)

A short, shareable map of the tools behind the system in this kit. Three ideas run through all of it: **route work by shape**, **externalize memory**, **automate the recurring**. Nothing here is required to use the kit — it's a menu you can borrow from.

## Core three
| Tool | What I use it for |
|------|-------------------|
| **Obsidian** | The vault itself — a local, Markdown, git-tracked knowledge base. The single source of truth everything else reads. |
| **Claude Code** | Primary AI agent — planning, architecture, writing PRDs/proposals/handoffs, running the pipeline. |
| **NotebookLM** | Turn a pile of sources into research, audio overviews, and slide decks. *(This session's deck was built with it.)* |

## AI agents — I route work by shape
| Tool | Best for |
|------|----------|
| **Claude Code** | Deep work: architecture, decisions, tradeoffs, multi-file changes. |
| **Codex CLI** | Bounded bug fixes (small, isolated, <2h). |
| **OpenCode** | Parallel tasks, and a second-opinion **validation** pass on code/proposals. |

## Memory & recall — so I don't hold it in my head
| Tool | Purpose |
|------|---------|
| **gbrain** | Semantic recall across the vault — "what did we decide about X?" beats grep. |
| **Smart Connections** (Obsidian) | "What else touches this note?" — related-note discovery. |
| **Session/user memory** | Agents remember across sessions (past work) and adapt to my preferences. |

## Capture & voice
| Tool | Purpose |
|------|---------|
| **Meeting pipeline** | Record → transcribe → vault note with Summary / Decisions / Action Items. |
| **VoiceMode** | Talk to the agent hands-free. |
| **voice-typed** *(custom)* | Hold a key, speak, text appears in any app. |

## Delivery (client work)
| Tool | Purpose |
|------|---------|
| **Google Workspace CLI** | Build estimate Sheets and proposal Docs programmatically. |
| **gh-axi** | GitHub operations, agent-friendly (issues, PRs, runs). |

## Obsidian plugins that pull their weight
**Dataview / DataviewJS** — live dashboards inside a note · **Excalidraw** — diagrams · **Iconic + Style Settings** — a legible, themed file tree.

---

## Custom systems I've built (short notes)

Small, purpose-built tools — each removes one recurring friction. The pattern to steal is the *shape*, not the specific tool.

- **voice-typed** — a background dictation daemon. Hold a hotkey, speak, and the text lands wherever the cursor is. Keeps a hot-reloaded vocabulary list so it spells project names right. *Why: typing is the slowest input; speaking drafts is 3× faster.*
- **RTK (token killer)** — a CLI proxy that filters verbose command output before it reaches the AI, cutting token cost ~20% on mixed work (60–90% on noisy commands). *Why: most tool output is noise the model doesn't need to pay for.*
- **Nightly digest** — a scheduled job that summarizes everything that changed in the vault each night into one readable brief. *Why: wake up already caught up.*
- **Status board sync** — regenerates a kanban board + active-threads view from a plain worklog every 30 minutes, zero API cost. *Why: status should be a byproduct of working, not a separate chore.*
- **Daily brief** — a ranked "next actions + pipeline health" note rebuilt on a schedule. *Why: start the day with the frog, not a blank page.*
- **Watchers** (finance, email triage, CI-minutes) — tiny daily crons that watch one thing and write a note when it matters. *Why: monitoring should page me, not the other way around.*

**The throughline:** if I do something more than twice, it becomes a script, a prompt, or a skill — and its output lands in the vault. The tools change; the habit is what compounds.
