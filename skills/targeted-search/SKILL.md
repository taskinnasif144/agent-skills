---
name: targeted-search
description: A lightweight multi-angle online search that returns a short summary shaped to the ask — one light interview round, 3 parallel angle-searchers, answer within about 5 minutes. Use when the user wants to search online and get a summary, asks a quick lookup or no-stakes question, or says "just find out" something. For a checked answer with challenged claims, use flash-research. For high-stakes decisions, deep dives, or maximum thoroughness, use verified-research. For background legwork saved to a file, use research. If it is genuinely unclear which one the user wants, ask "summary, quick pass, or full deep research?" before starting.
---

# Targeted Search

## What this skill is for

The user wants an online search with a short summary, not a research report.
This skill runs a light interview, searches from several angles in parallel,
and writes a summary shaped to the question. The whole run finishes within
about 5 minutes.

## When to use which

- **This skill:** "search online and give me a summary", quick lookups,
  no-stakes questions, "just find out".
- **flash-research:** a checked answer with challenged claims ("quickly",
  "briefly", single-claim fact-checks).
- **verified-research:** career, money, or long-term decisions, deep dives,
  maximum thoroughness.
- **research:** background legwork saved to a Markdown file.
- Naming a skill explicitly always wins over these rules.
- If it is genuinely unclear which one the user wants, ask the routing pick
  through the question tool — "Summary, quick pass, or full deep research?" —
  and run the one they pick.

## The pipeline

1. Grill lightly (one round)
2. Plan the angles
3. Search, in parallel (3 searchers)
4. Write the summary

---

## Step 1: Grill lightly (one round, then go)

Ask ONE question-tool round of 2 to 3 questions. Give concrete options, put
the recommended option first, and label it "(Recommended)".

- What is the summary for? What will they do with it?
- What counts as a done answer? (a comparison, a yes/no, a list, a fact?)
- Anything out of scope?

Do not search before this round. Do not ask for confirmation after it — say
what you will search in one line and start. For a clear, simple ask, one
question is enough.

## Step 2: Plan the angles

Write a quick internal plan. Do not show it.

- Split the ask into 2 to 4 search angles. Give each angle a different
  framing, for example: the direct answer, recent or primary sources,
  alternatives or counterexamples, regional or niche perspectives.
- Note a freshness window: fast-moving topics (news, tools, salaries):
  6 to 12 months. Stable topics: older is fine.

## Step 3: Search, in parallel

Spawn 3 **Searcher** subagents at the same time, one angle each. Time-box
the whole wave so the summary is ready within about 5 minutes:

- Each Searcher: at most 8 varied queries, open at most 5 pages, return
  within about 2 minutes. Prefer primary sources (docs, papers, datasets,
  filings) over write-ups. Take the best evidence you find in time — do not
  read forever.
- Each Searcher returns findings as: **claim, source URL, publisher,
  publication date, and whether it is data or commentary.** Drop anything
  with no URL or no date.

## Step 4: Write the summary

Write the summary in the chat. 150 to 300 words. Shape it to the question
type:

- A comparison: side by side, then a one-line verdict.
- A fact or yes/no: the answer first, then the context that matters.
- An overview: bullets, strongest finding first.

Always end with the sources actually used: link and date. Do not write the
summary to a file.

---

## Rules that always apply

- Judge a source by how its data was produced, never by how polished,
  popular, or prominent the page is. Marketing-tier content (vendor blogs,
  SEO listicles, affiliate rankings, sponsored posts, PR releases) never
  proves a number, however widely repeated. The primary source outranks
  every secondary retelling.
- Never invent a source, number, or date. If you cannot find it, say so.
- If good evidence is thin, say so. Never fill gaps with guesses.
- Never treat a search snippet as verified. Open the page and check.
- Ask the user every question through the question tool. If the harness has
  no question tool, fall back to numbered questions in chat.
- State today's date and the data window if the topic is time-sensitive.
- Do not narrate the machinery (agent names, phases) in the final answer.
- Paraphrase sources. Do not paste long quotes.

---

## Subagent brief

**Searcher**
"Search this angle: [angle] for the ask: [ask]. Context: [grill summary].
Freshness window: [window]. At most 8 varied queries, open at most 5 pages,
finish within about 2 minutes. Prefer primary sources (docs, papers,
datasets, filings). Return each finding as: claim, source URL, publisher,
publication date, data or commentary. Drop anything with no URL or date."
