---
name: flash-research
description: A quick, lighter pass of verified-research with the same accuracy rules — interviews the user, searches from several angles, challenges every claim — but a smaller agent pipeline and a 250 to 400 word answer, done in about 3 to 5 minutes of agent work. Use this skill when the user wants research "quickly", "briefly", "in short", asks a simple current-fact question or a single-claim fact-check, or says the full treatment is overkill. For high-stakes decisions (career, money, long-term commitments), deep dives, or maximum thoroughness, use verified-research instead. If it is genuinely unclear which one the user wants, ask "quick flash pass or full deep research?" before starting.
---

# Flash Research

## What this skill is for

The user wants a checked answer now, not a deep dive. This skill holds the
same accuracy bar as verified-research — multiple angles, challenged claims,
labeled evidence — on a smaller pipeline: about 4 subagent dispatches instead
of 7 to 11, and a 250 to 400 word answer instead of 600 to 800.

The interview is the same one verified-research runs. It is what makes the
answer fit the user, so it stays in full. All the heavy work stays hidden.
Only the short final answer reaches the user.

## When to use which

- **This skill:** "quickly", "briefly", "in short", simple current-fact
  questions, single-claim fact-checks, and any question where the user says
  the full treatment is overkill.
- **verified-research:** career, money, or long-term decisions, deep dives,
  and any request for maximum thoroughness.
- Naming either skill explicitly always wins over these rules.
- If it is genuinely unclear which one the user wants, ask one question —
  "Quick flash pass or full deep research?" — and run the one they pick.

## The pipeline

1. Grill the user
2. Plan
3. Scout sources (only when needed)
4. Collect, in parallel (3 Collectors)
5. Form assumptions
6. Challenge (1 Skeptic)
7. Verify while writing
8. Write the answer

---

## Step 1: Grill the user (always, before any searching)

Do not search yet. The same question gets a different answer for different
people, so interview the user about THIS question first.

Ask about whatever would change the answer. Usually that means:

- **The decision:** what will they do with the answer? What is at stake?
- **Their situation:** experience level, current skills, goal or target role,
  country or job market, timeline, time per week, money or other limits.
- **What they already believe:** what have they heard or assumed? These
  become claims to test.
- **What a good answer looks like:** a recommendation, a yes/no, a ranked
  list, a fact-check?
- **Scope:** anything they do not care about.

How to grill:

- Ask in small rounds of 3 to 5 questions. Use tappable options if the app
  supports them. Otherwise use numbered questions with short options.
- Do not ask what you can find out yourself by searching.
- For a pure fact-check, ask less: the exact claim, who said it, when, and
  where.
- Keep going until you can explain their question back in one short paragraph.
  Then say it back: "Here is what I will research: ...". Wait for a yes.
- Stop when more questions would not change the research.

## Step 2: Plan

Write a quick internal plan. Do not show it to the user.

- Split the question into 3 to 6 sub-questions.
- Set a **freshness window for each sub-question**, based on the topic:
  - Fast-moving (job market, salaries, tools, AI, news): 6 to 12 months.
  - Medium (industry practices, frameworks): up to 2 years.
  - Stable (fundamentals, history): older is fine, but confirm it still holds.
- Decide which source types fit each sub-question.

## Step 3: Scout sources (only when source quality matters)

For job postings, salaries, hiring trends, or anything where some sources are
much better than others: if you are not already sure which sources to trust,
spawn a **Source Scout** subagent BEFORE collecting.

The Scout battle-tests candidate sources. It checks:

- Is the data real (actual postings, survey responses, filings) or just opinion?
- How big is the sample? How recent is it? Who runs it and who pays for it?
- Is the method public?
- Do independent sources agree on a number that can be checked?

It returns a short list: trusted, usable with caution, do not use. Collectors
use only the trusted and cautious lists for hard data.

For general topics, prefer sources in this order: primary source (the original
data, filing, paper, or official page), then data-backed reporting, then
expert opinion. Opinion is never evidence for a number.

## Step 4: Collect, in parallel

Spawn 3 **Collector** subagents at the same time. Give each a different
angle:

- Hard data (postings, surveys, statistics)
- Practitioner and expert views
- Recent changes, news, and alternatives the user did not mention

Each Collector must:

- Generate varied search queries: different wording, synonyms, region terms,
  "vs" comparisons, negative framings, year-specific terms.
- Return every finding as: **claim, number (if any), source URL, publisher,
  publication date, date of the data itself, source type, and how it was
  measured.**
- Keep data and commentary separate. Never present an opinion as a fact.
- Drop any claim that has no URL or no date.

## Step 5: Form assumptions

Read all Collector findings. Write 2 to 5 working assumptions. These are your
draft answer. Write each as a statement that can be proven wrong.

## Step 6: Challenge

Spawn 1 **Skeptic** subagent and give it every assumption. Its job is to
break each one:

- Search for the opposite claim and for newer data that contradicts it.
- Look for better alternatives the Collectors missed.
- Find who disagrees and why.
- Find the conditions where the assumption fails.
- Check for conflicts of interest in the source (a bootcamp selling courses,
  a vendor selling a tool).

The Skeptic reports one verdict per assumption: **holds, weakened, or
broken**, with evidence and links.

If a key assumption is broken (one the bottom line rests on), revise it and do
one targeted re-search round yourself, without spawning new subagents. That one
round is the maximum; when it finishes, move to the write-up.

## Step 7: Verify while writing

Do the verification yourself as you draft the answer. This skill has no
Verifier subagent. Apply these rules to every claim as you write. A claim
counts as **solid** only if ALL of these are true:

- At least 2 independent sources support it. Sources that copy each other, or
  trace back to the same original dataset, count as ONE source.
- It is inside its freshness window.
- The source type is trustworthy for that kind of claim.
- It survived the Skeptic.
- The source is not selling what the claim promotes (a bootcamp selling
  courses, a vendor selling a tool).

Also:

- Trace every number the answer leans on back to its original source. Do not
  trust a number that is only repeated across articles.
- Check dates twice: when it was published and when the data was collected.
- Label each claim: **Confirmed, Likely, Disputed, Unverified, or False.**
- Throw away claims that are single-source, undated, unsourced, or outdated.
- If good evidence is thin, say so. Never fill gaps with guesses.

## Step 8: Write the answer

### How to write (read this carefully)

Write for a reader who stopped following somewhere and needs you to back up.
This is not "be brief". Brief writing that clips words makes people more lost.

- Use plain English. One idea per sentence. Common words. Active voice.
- Explain any jargon or acronym in a few words the first time it appears.
- Add the background the reader is missing. Do not assume they know it.
- Say why a number matters, not just what it is.
- Use the user's own words and situation from the interview.
- Never write "it depends" without saying what it depends on.
- Write full sentences, not clipped fragments.
- Cut the lowest-value details to stay short. Never cut clarity.

### Length

About 250 to 400 words.

### Format

**Bottom line**
Two or three sentences. Answer the question directly. For a decision, say
what to do and the first step to take.

**What the data says**
2 to 4 bullets. Each has the claim label (**Confirmed, Likely, Disputed,
Unverified, or False**), the number (with unit and year), what it means in
plain words, and the source with its date.

**What does not hold up**
Claims or common beliefs that failed checking, and why. Then the strongest
case against the bottom line, and when it would be the right one.

**Confidence and sources**
One line: High, Medium, or Low, and the main reason. Then a compact list of
only the sources actually used: link and date.

---

## Rules that always apply

- Never invent a source, number, or date. If you cannot find it, say so.
- Never treat a search snippet as verified. Open the page and check.
- Tell the user today's date and the data window used if the topic is
  time-sensitive.
- If a tool fails or something could not be checked, say exactly what.
- Write the answer in the chat. Do not write the answer or the raw findings
  to a file.
- Do not narrate the machinery (agent names, phases) in the final answer.
  One short line is fine, for example: "Checked 9 sources and challenged
  4 assumptions."
- Paraphrase sources. Do not paste long quotes.

---

## Subagent briefs

Use these as starting prompts. Adapt them to the question.

**Source Scout**
"Find the main sources for [topic]. For each one, check how its data is
produced, its sample size, recency, who runs it and who funds it, and whether
its numbers match other sources. Return three lists: trusted, usable with
caution, do not use. Give one line of reasoning per source."

**Collector**
"Research this angle: [angle] for the question: [question]. Context about the
user: [interview summary]. Freshness window: [window]. Use varied search
queries. Return each finding as: claim, number, source URL, publisher,
publication date, data date, source type, method. Separate data from opinion.
Drop anything with no URL or date."

**Skeptic**
"Here are the assumptions: [list]. Try to prove each one wrong. Search for the
opposite claim, newer contradicting data, better alternatives, who disagrees,
conditions where it fails, and conflicts of interest. Return holds, weakened,
or broken for each, with evidence and links."

---

This skill is the light sibling of verified-research. The two share the same
interview and the same accuracy rules; when you change one, change the other.
