# How to Use This Kit — and get the best out of it

The single most important habit: **your knowledge base (the vault) is the source of truth, and your AI agent must start from it every session.** Everything else in this kit only works if that holds. This page is the discipline that turns a folder of templates into a system.

## The golden rule

**One vault. One source of truth. Anchor every session to it, and write everything back into it.** If work happens outside the vault — in a chat window, a scratch file, someone's head — it's lost to both you and the agent. If it isn't in the vault, it didn't happen.

## Day-one setup (once)

1. **Pick a home for your vault** — a folder, git-tracked. Copy [`example-vault/`](example-vault/) as your starting shape and rename it.
2. **Tell your agent where it lives and that it is the source of truth.** Paste the *pin* below into your agent's standing instructions — the file it reads automatically every session (`CLAUDE.md` for Claude Code, `.cursorrules` for Cursor, `AGENTS.md`, a system prompt, etc.). This is the step most people skip, and it's the one that makes or breaks the whole thing.
3. **Seed it** — create `index.md` (the map) and a `work/<project>/context.md` for your first real project. Then run a brief through the [`prompts/`](prompts/).

## The pin — paste this into your agent's standing instructions

```
This project's knowledge base ("the vault") is at <PATH-TO-YOUR-VAULT>.
It is the SINGLE SOURCE OF TRUTH. Follow these rules every session:

1. START HERE. Before doing anything, read `index.md`, then the relevant
   `work/<project>/context.md`. Arrive oriented; never ask me to re-explain
   a project whose context is already in the vault.
2. ROUTE BY TYPE. Every artifact goes in its typed folder — PRD → proposals/,
   decision → decisions/, meeting → meetings/, dev spec → handoffs/, research →
   notes/. Never write files loose at a folder root.
3. CAPTURE THE WHY. When I decide something, write a decision file
   (Context / Decision / Consequences). A decision without its reasoning is
   noise.
4. KEEP CONTEXT LIVING. Update `context.md` in place. Never spawn context-v2
   or a duplicate — one living doc per project.
5. LINK. Connect related notes so the vault is a graph, not a pile.
6. DON'T INVENT. If information is missing, ask me. Never fill a gap with a
   guess and never leave the structure half-built.
```

## Daily discipline — do / don't

**DO**
- Start every session by reading the vault (`index.md` → project `context.md`).
- Put every artifact in its typed folder, and reuse the same topic name across `decisions/` and `notes/`.
- Write decisions with their *why*.
- Keep `context.md` current — update it in place after every meaningful change.
- Link related notes.
- Turn every meeting and every piece of client feedback into a note with owned action items.
- Empty `inbox/` weekly — promote captures into the right folder.

**DON'T**
- Don't let the agent write files wherever it likes — unrouted files are how structure rots.
- Don't spawn `context-v2` or duplicate docs — update the living one; archive the superseded.
- Don't record a decision without the *why* — future-you can't reconstruct it.
- Don't keep knowledge in chat only — move it into the vault before the session ends.
- Don't fork topic names (`proposal` vs `proposals`, `wurzburg` vs `würzburg`) — one subject, one folder.

## Why this matters

An AI agent is only as good as the context it can read. A **structured, linked vault** means the agent arrives already oriented and gives sharp, grounded output. An **unstructured pile** means it guesses, misses, contradicts itself, and drifts — and you're back to holding every project in your own head, which is the exact problem this kit removes. The structure is not overhead; the structure is what makes the AI useful. **The discipline is the product.**

## Healthy-vault checklist (run it weekly)

- [ ] `index.md` points to every active project.
- [ ] Each project has a current `context.md` (updated, not stale).
- [ ] Every decision is a dated file that states its *why*.
- [ ] No loose files at folder roots — everything sits in a typed subfolder.
- [ ] No duplicate or superseded doc left beside the live one (archive them).
- [ ] `inbox/` emptied this week.

If all six hold, your agent will consistently give you its best. If they don't, fix the structure first — the output quality follows the structure, every time.
