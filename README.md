# agent-skills

Installable agent skills for the [skills](https://skills.sh) ecosystem (`npx skills`).

## Which one do I need?

| | targeted-search | flash-research | verified-research |
|---|---|---|---|
| Use for | Online search with a short summary, quick lookups, no stakes | Quick passes, simple current-fact questions, single-claim fact-checks | Career/money/high-stakes decisions, deep dives, maximum thoroughness |
| Pipeline | ~3 subagents (3 angle-searchers), one light grill round | ~5 subagents (source scout, 3 collectors, 1 skeptic) | 8–11 subagents (source scout, collect, challenge, verify) |
| Answer | 150–300 word chat summary shaped to the ask | 250–400 words, 4 sections | 600–800 words, 7 sections |
| Time | About 5 minutes total | About 3–5 minutes of agent work | About 5 minutes read, longer to research |

All three interview you first and search from multiple angles. flash-research and verified-research also challenge their own claims and label what holds up; targeted-search returns a plain summary. A fourth skill, research, runs in the background and saves findings to a file. Not sure which? The agent will ask you; naming a skill explicitly always wins.

## targeted-search

A lightweight multi-angle online search: one light interview round, 3 parallel angle-searchers, and a 150–300 word summary shaped to your question — done in about 5 minutes.

### Install

```bash
npx skills add taskinnasif144/agent-skills --skill targeted-search
```

### Example

Ask: "Search online and summarize: what changed in React Server Components this year?" The skill asks 2–3 quick questions, searches from three angles in parallel, and returns a short summary with sources.

## flash-research

A quick, lighter pass of verified-research with the same accuracy rules — interviews you, searches from several angles, challenges every claim — but a smaller agent pipeline and a 250–400 word answer.

### Install

```bash
npx skills add taskinnasif144/agent-skills --skill flash-research
```

### Example

Ask: "Quickly — is TypeScript still the default choice for new web projects in 2026?" The skill interviews you in a few short rounds first, searches data, expert views, and recent changes, challenges the findings, and returns a labeled 250–400 word answer.

## verified-research

Replaces hours of manual online research with a short, plain-English answer that has been challenged and cross-checked — readable in about 5 minutes. The skill interviews you first, then gathers evidence in parallel, attacks its own assumptions, and verifies only fresh, well-sourced claims before writing a 600–800 word answer with a bottom line, the data, what doesn't hold up, the strongest counter-case, next steps, confidence, and sources.

### Install

```bash
npx skills add taskinnasif144/agent-skills --skill verified-research
```

### Example

Ask: "Is LeetCode still relevant for interviews in 2026?" The skill grills you about your target role and market first, researches the question, challenges its own findings, and returns a checked answer with sources, readable in about 5 minutes.

### Adding more skills

Drop new skills under `skills/<skill-name>/SKILL.md` (folder name matches the `name:` frontmatter). The `npx skills` CLI discovers them automatically.
