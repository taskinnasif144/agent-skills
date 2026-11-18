---
name: requirement-grill
description: Turn a rough feature idea into a confirmed requirements summary. Use when the user invokes requirement-grill with or without an idea. User-invoked only.
disable-model-invocation: true
---

# Requirement Grill

Turn a rough software idea into a clear requirements summary. You do not design the system, write specs, or implement. You identify the problem, fill the gaps with guided questions, check feasibility when needed, and deliver one summary.

## Standing rule (non-negotiable)

**Every question you ask the user goes through the question tool.** Never ask questions in free text. Use grilling-style numbered rounds: several related questions per round, each with a recommended answer first (`➡️`). Wait for answers before the next round. This applies to every phase below.

## Step 1 — Get the rough idea

- If the skill was invoked with text, that text is the rough idea.
- If invoked with no text: first question-tool question — “Paste your rough idea.”

## Step 2 — Gap-filling rounds (question tool only)

Run question-tool rounds until no open decisions remain. You must cover:

1. **Problem** — what pain or need does this solve?
2. **Who it serves** — the users/beneficiaries.
3. **Success criteria** — how we know it works.
4. **Constraints / limits** — the user’s stated limits only (cost, time, platforms, team).
5. **Direction** — offer **2–3 direction options** with trade-offs and one **recommended** answer.
6. **Out of scope** — what explicitly will NOT be built.

Do not read files yet. This step is pure chat.

## Step 3 — Perfect prompt

Assemble the gap-filled answers into one complete, clean requirements prompt (the “perfect prompt”). Print it in chat, then continue automatically — no approval gate.

## Step 4 — Codebase pass (only if a project is open)

Read the code and files that are relevant to this feature (structure, existing similar features, stack, patterns). Then:

- If the code raises new gaps or contradicts the perfect prompt (stack already fixed, feature half-exists, hidden constraints): **re-ask via question-tool rounds**, then update the perfect prompt in place (print the changed parts).
- If nothing is open or nothing relevant exists: skip this step.

Read only what is relevant. No broad exploration.

## Step 5 — Feasibility check (conditional, online)

Run a web search **only when unsure or unclear**: the idea depends on an external or unknown dependency — an external API, a paid service, a platform limit, a new library, or browser/OS support. If everything is already known and internal, skip this step entirely.

When running it:

- Search the web for whether the dependency/capability exists and works under the user’s stated limits.
- Verdict is exactly one of:
  - `FEASIBLE`
  - `FEASIBLE WITH CONSTRAINTS` — list every constraint
  - `NOT FEASIBLE` — provide alternatives
- “100% feasible given our constraints” means `FEASIBLE`, or `FEASIBLE WITH CONSTRAINTS` where the user accepts the constraints in the summary.

Do not search for open-source replacements or “should I build this” alternatives — feasibility only.

## Step 6 — Summary (print once, no revise loop)

Write the summary in **ASD-STE100 Simplified Technical English** (short sentences, common words, one idea per sentence). Structure exactly:

1. **Context** — the situation, a little background
2. **Problem** — the problem this feature solves
3. **Who it serves** — beneficiaries
4. **Success criteria** — what “done and working” means
5. **Direction chosen** — which of the 2–3 options, and why
6. **Scope / Out of scope** — what is in, what is out
7. **Feasibility** — only if Step 5 ran: verdict + constraints + sources checked

Print the summary **once**. Do not ask for approval. Do not loop on revisions unless the user brings a change themselves.

## Step 7 — Single ending question (question tool)

One question-tool question only:

- **Stop** — end here
- **Continue to `/dev`** — tell the user to run `/dev` in their project and paste this summary when functionality grilling starts

## Never do this

- No spike / bounded / architectural classification
- No spec files, no docs written, no commits
- No `writing-plans` handoff
- No implementation, no code
- No open-source / tool / build-vs-buy alternative checks
- No auto-triggering — this skill runs only when the user invokes it
- No free-text questions — question tool, always
