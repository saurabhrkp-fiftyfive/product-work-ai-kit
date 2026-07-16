# Developer Workflows — the same system, dev-shaped

The pipeline in this kit reads as PM/lead territory: PRD, proposal, estimate. But the vault + agent pattern works just as well for the person *building* the thing. This file maps the same three pillars — pipeline, memory, capture — onto everyday development work: frontend, backend, anywhere code is written.

**The shift is identical:** stop re-deriving context in your head; make the agent start from written state.

## 1. Handoff → implementation

The handoff note (last pipeline stage) is your entry point, not a ticket title.

> **Prompt:** "Read `handoffs/<feature>.md` and `work/<project>/context.md`. Restate what you're going to build and what the acceptance criteria are. Ask me about anything ambiguous BEFORE writing code."

Why it works: the agent reads the same spec the lead wrote — no telephone game. Ambiguities surface as questions, not as wrong code.

## 2. Design → component (frontend)

Screenshots and design files are input artifacts like any brief.

> **Prompt:** "Here's the design (screenshot/link). Scaffold the component: props from the data it displays, states (loading/empty/error), and match the conventions in `knowledge/frontend-conventions.md`. List what the design doesn't specify."

Keep a `knowledge/frontend-conventions.md` in your vault — design tokens, naming, component structure, state-management choices. The agent reads it every time; your components stop drifting.

## 3. Test-first loop

> **Prompt:** "Write the failing tests for the acceptance criteria in the handoff first. Show me the tests. Only after I approve, implement until they pass."

Why: the acceptance criteria are already written (pipeline!), so tests fall out of them. The agent can't quietly redefine "done."

## 4. Debug with a written trail

When a bug bites, resist pasting the error and hoping.

> **Prompt:** "Symptom: <what you see>. Read the relevant code and list the 3 most likely root causes ranked. Verify the top one with evidence before proposing a fix."

If the fix reveals something non-obvious — a gotcha, a constraint, a wrong assumption in the docs — write it down: `notes/<topic>/` or `knowledge/`. Next dev (or next agent session) doesn't re-learn it.

## 5. Second-agent PR review

The validation loop from [`starter-kit.md`](starter-kit.md) applied to code:

> **Prompt (to a DIFFERENT agent):** "Review this diff against the handoff spec and our conventions. Hunt for correctness bugs, missed acceptance criteria, and anything that will confuse the next reader. Refute your own findings before reporting."

Generate with one, validate with another, document the verdict. A fresh agent doesn't share the first one's assumptions — that's the whole value.

## 6. Decisions live in the vault — yours too

"Why is this component structured this way?" is the frontend version of "why did we build it this way?" Architectural choices you make while coding — state library, folder structure, CSS approach — get a decision file (`decisions/<topic>/`), same Context/Decision/Consequences format. Two lines is enough. Future-you and every agent session after gets the why for free.

---

**Start small:** pick ONE loop (handoff → implementation is the easiest win), run it on your next real ticket, and let the rest follow. Same rule as everything in this kit: if it isn't written down, the agent can't read it — and neither can the next human.
