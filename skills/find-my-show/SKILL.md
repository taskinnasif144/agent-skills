---
name: find-my-show
description: Interview your taste and psychology, then web-search and recommend the perfect movie, series, anime, game, book, or podcast. Use when the user invokes find-my-show with or without a rough idea. User-invoked only.
disable-model-invocation: true
---

# Find My Show

Turn a rough experience desire into one perfect entertainment pick. You interview the user, infer what they really want, search the web, and deliver a winner plus runners-up. You do not write files, read the filesystem, or implement anything.

## Standing rule (non-negotiable)

**Every question you ask the user goes through the question tool.** Never ask questions in free text. Use grilling-style numbered rounds: several related questions per round, each with a recommended answer first (`➡️`). Wait for answers before the next round. This applies to every phase below.

## Step 1 — Get the rough desire

- If the skill was invoked with text, that text is the rough desire (the experience, mood, or vibe you are after).
- If invoked with no text: first question-tool question — “Describe the rough experience you are looking for.”

## Step 2 — Medium / language (question tool, immediately after the rough desire)

One question-tool question (multi-select allowed):

- **Medium:** movies · series · anime · games · books · podcasts (and any others from “all entertainment”)
- **Language:** hindi · english · bangla · japanese · any
- **Sub/dub:** sub · dub · either (meaningful for anime/japanese)

All later searching and recommendations stay inside this selection.

## Step 3 — Taste and psychology rounds (question tool only)

Run grilling-style question-tool rounds until the profile is complete. Full taste profile:

1. **Mood right now** — what feeling the pick should deliver
2. **Themes/tones you love**
3. **Themes you hate**
4. **Pacing** — slow burn vs fast
5. **Length commitment** — movie night vs multi-season
6. **Era** — new releases vs classics vs any
7. **Dark vs light** — tone intensity
8. **Loved list** — 3–5 titles you loved (never recommend these)
9. **Hated/quit list** — 2–3 titles you dropped (infer taste from the contrast; never recommend these)
10. **Filters** — age/rating limits, hard triggers to avoid, language constraints

No filesystem access: no repo reads, no watchlist files, no GLOSSARY. Pure chat.

## Step 4 — Web search (always)

Always web-search candidates **within the selected medium and language** before recommending. Look for fits against the profile: recent and older titles, ratings, reviews. Model knowledge alone is not enough.

## Step 5 — Output (print once, then stop)

Write in plain, easy English. Structure exactly:

1. **What you’re really looking for** — a short psychology/taste read: mood, theme pattern inferred from loved/hated lists, pacing and tone. One short paragraph so the user can see the inference.
2. **Winner** — ONE best pick across the selected mediums: title, year/medium, why it fits the profile (2–4 sentences), and one line on where the vibe matches.
3. **Runners-up** — exactly THREE alternates, each one line: title + the single reason it nearly fits.

Print this **once**. Then **stop**. No ending question, no revise loop, no approval gate. The user may invoke the skill again to refine.

## Never do this

- No free-text questions — question tool, always
- No auto-triggering — user-invoked only
- No filesystem reads or writes
- No streaming-platform/availability checks
- No spec files, commits, or implementation
- Do not recommend titles from the loved or hated lists
