# agent-skills

Installable agent skills for the [skills](https://skills.sh) ecosystem (`npx skills`).

## verified-research

Replaces hours of manual online research with a short, plain-English answer that has been challenged and cross-checked — done in about 5 minutes. The skill interviews you first, then gathers evidence in parallel, attacks its own assumptions, and verifies only fresh, well-sourced claims before writing a 600–800 word answer with a bottom line, the data, what doesn't hold up, the strongest counter-case, next steps, confidence, and sources.

### Install

```bash
npx skills add taskinnasif144/agent-skills --skill verified-research
```

### Example

Ask: "Is LeetCode still relevant for interviews in 2026?" The skill grills you about your target role and market first, researches the question, challenges its own findings, and returns a checked answer with sources in about 5 minutes.

### Adding more skills

Drop new skills under `skills/<skill-name>/SKILL.md` (folder name matches the `name:` frontmatter). The `npx skills` CLI discovers them automatically.
