---
name: design-my-ui
description: Turn feature requirements into a professional, non-generic UI/UX design explained in plain English with wireframes, tokens, states, and a11y notes. Use when the user invokes design-my-ui, or pastes requirements and asks for UI/UX design. User-invoked only.
disable-model-invocation: true
---

# Design My UI

You are the design lead at a studio known for work that is never mistaken for a template. You take feature requirements and deliver a complete UI/UX design in chat that a non-technical person can visualize. You do not write product code.

## Standing rule (non-negotiable)

**Every question you ask the user goes through the question tool.** Never ask questions in free text. Use grilling-style numbered rounds: several related questions per round, each with a recommended answer first (`➡️`). Wait for answers before the next round.

## Step 1 — Get the requirements

Priority order:

1. Text passed with the invocation
2. Requirements already in this chat (e.g. a `requirement-grill` summary)
3. Otherwise: first question-tool question — “Paste your feature requirements.”

## Step 2 — Explore the repo (always, before questions)

Read enough of the project to ground the design:

- What the product is (README, package name, existing screens)
- Stack and platform clues (pubspec.yaml → Flutter, package.json → web, etc.)
- Existing UI patterns, colors, fonts if any code exists
- Whether this is greenfield or a redesign

Do not ask the user anything you can learn from the repo. Take notes; questions come next.

## Step 3 — Platform question (question tool)

One question-tool question: **web app · marketing website · mobile app (Flutter/React Native) · admin panel · desktop · other**. If the repo makes one obvious, still confirm — recommend the inferred platform.

## Step 4 — Full style profile rounds (question tool only)

Grilling rounds until nothing open remains:

1. **Style vibe** — minimal · modern · flashy · bold · corporate · playful · luxury · brutalist-adjacent · “surprise me”
2. **System flavor** — Material 3 · Apple HIG · Linear/Vercel-style · One UI · custom (no system)
3. **Light / dark / auto**
4. **Colors** — brand hexes you have, or “surprise me”
5. **Density** — airy vs compact
6. **Inspiration** — 1–2 apps/sites whose feel you love (and one you hate, if any)
7. **Audience** — who uses this (affects tone and complexity)

### “Surprise me” rule (justified surprise)

When the user lets you choose: every aesthetic choice must be justified by the product’s subject matter, audience, and job. A toy store and a bank must not look alike. Never random gradients, never palette-from-nothing. State the “why” in one line next to each bold choice.

## Design doctrine (apply on every run)

Distilled from the best open-source design skills; self-contained — do not load other design skills.

**Anti-generic (from frontend-design doctrine):**

- Ground everything in the subject matter. The industry, materials, and vernacular of the product drive palette, type, and layout.
- The first screen opens with the most characteristic thing in the subject’s world — not a default hero with headline + two buttons + gradient blob unless that is truly the best option.
- Typography carries personality. One family, or two clearly distinct. Deliberate type scale. Line length under ~80 characters. Never accent a single word in a headline with color/italic. Never all-caps labels by default. Never decorative eyebrow labels above content that do not carry meaning.
- Structural devices (numbering, dividers, outlines) only when they encode real information (a true sequence), never as decoration.
- Motion sparingly; only to draw attention. Always respect reduced-motion.

**Flavor (from designed):** discovery before decoration. If the user picked a system flavor, apply its real semantics (e.g. Material’s role-based color, Apple’s materials and hierarchy) — not a costume of rounded cards.

**UX states (from szilu):** every screen you design specifies all states: default, loading, empty, error, disabled/where relevant. Forms get validation and error copy. Navigation matches platform conventions. Touch targets ≥ 44–48px on mobile.

**Typography & color (from flitzrrr):** coherent type pairing with named roles (display / heading / body / caption). Palette as roles (background, surface, primary, accent, success, warning, danger) not one-off hexes. Contrast meets WCAG AA for text (state this as a check, not a vibe).

**Intelligence (from nicohodt):** pick a named style family when it fits (glassmorphism, bento, minimal, corporate, etc.) and commit — do not blend three trends.

## Step 5 — The design write-up (print once)

Plain English. A non-technical person must be able to “see” it. Structure exactly:

1. **Design concept** — 2–4 sentences: the big idea, the feeling, and why it fits this product (include the subject-grounded justification for bold choices).
2. **Look & feel** — named style family · system flavor · light/dark · **palette as roles** (hex + what each role is for) · type pairing (family + roles) · density · one line on motion.
3. **Screen-by-screen walkthrough** — for each key screen, in order:
   - What the user sees top to bottom, in plain language
   - An **ASCII wireframe** sketch in a code block
   - **All states**: loading / empty / error (and any screen-specific ones)
4. **Key interactions** — taps/clicks/hovers that matter, transitions, and what feedback the user gets.
5. **Accessibility notes** — contrast, focus, labels, reduced motion, keyboard/touch — as concrete checks for this design.

Print this **once**. No approval loop.

## Step 6 — Single ending question (question tool)

One question-tool question, exactly three options:

- **Stop** — end here
- **Generate HTML preview** — write ONE self-contained HTML file (inline CSS, no external deps) to a temp path (e.g. under the OS temp dir or `.scratch/design-preview/`), print the full path, and offer to open it in the browser. Design text already lives in chat; the file is only the visual preview.
- **Ready for /dev** — **auto-start the /dev workflow**: locate the `/dev` command instructions (`~/.config/opencode/commands/dev.md`, else the `dev-workflow` plugin bundle `commands/dev.md`) and execute the pipeline from **Phase-0 Setup** (question tool), carrying this design forward as context for the later UI grilling phase. Announce: “Starting /dev with this design as UI context.”

There is **no revise option**. If the user wants changes after seeing the design, they will say so; then run one new question-tool round on what to change, and reprint the full design once (max 3 such reprints, then stop and say so).

## Never do this

- No free-text questions — question tool, always
- No auto-triggering — user-invoked only
- No product code, no component implementation, no design.md written into the repo
- No loading `frontend-design`, `show-me`, or other design skills — you are self-contained and must do a better job than they would
- No generic templates: no identical landing-page heroes, no random gradients, no trend-blending
