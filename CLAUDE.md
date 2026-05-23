# Project: Marcos — Interactive Bilingual Bible Study Tool

A single-page HTML tool for studying the Gospel of Mark in Spanish (NTV) alongside the Greek. Built for a learner of Latin American Spanish.

The whole app is one file: `index.html`. It is loaded directly in the browser — no build step, no framework.

## Features (already built, do not break)

- **Color-coded verbs** by tense: presente, pretérito, imperfecto, futuro, imperativo. Each tense has a distinct color and a legend at the top.
- **Click any word** → popup with part-of-speech, grammar analysis, and (for verbs) a Latin American conjugation table (yo / tú / usted-él-ella / nosotros / ustedes-ellos-ellas — never `vosotros`).
- **Word analysis is dynamic.** On click, the page calls the Anthropic API (`claude-sonnet-4-20250514`) for a fresh JSON analysis of any word in the passage. A small `WORD_DATA` object provides fallback content if the API is unreachable.
- **Audio pronunciation** via ResponsiveVoice with a Spanish voice (prefers Latin American locales).
- **Tutor chat panel** at the bottom that answers questions about the passage's Spanish grammar, vocabulary, and translation choices. The system prompt enforces Latin American conventions.

## Current state

- Covers Marcos 1:1–3 only.
- Cosmetic notes: there's a stray CSS block near the `.speak-btn` rules (around `font-style: italic; color: var(--gold);`) that looks like leftover from a deleted selector. Worth tidying but not urgent.
- HTML comment at top says `<!-- v3 -->` but this is actually v17. Update if convenient.

## Goals, in order

1. **Publish online via GitHub Pages.** This is the primary reason the project moved to Claude Code. The file is already named `index.html` — should be near-zero config to deploy.
2. **Extend coverage to Marcos 1:1–15.** I will provide additional NTV Spanish and Greek text. When extending the passage in the HTML:
   - Preserve the existing verse-numbering pattern (`<span class="verse-num">N</span>`).
   - Wrap every word in a `<span class="word ...">` with the appropriate POS class (`verb-present`, `noun`, `article`, etc.) and a `data-word="..."` attribute.
   - Verb-tense classes determine the color — pick the right one for each verb.
   - Update the Greek text in the `PASSAGE_CONTEXT` constant in the chat system prompt to match.
3. **Long-term:** extend to the rest of Mark, chapter by chapter. Eventually consider splitting into per-chapter files with a small index page.

## Constraints

- **No frameworks unless I ask.** This is intentionally a single static HTML file. Don't introduce React, a bundler, or npm dependencies. Vanilla JS only.
- **Latin American Spanish throughout.** Never use `vosotros`. All grammar explanations, verb forms, and usage notes assume Latin American conventions.
- **The Anthropic API key cannot be embedded in a public site.** When you set up publishing, flag this — the dynamic word analysis and chat panel call the API directly from the browser with `anthropic-dangerous-direct-browser-access: true`. On a public GitHub Pages deployment, users would need to supply their own key (or we add a minimal proxy). Discuss with me before settling on an approach.
- **Don't paraphrase source text.** When I provide Greek or Spanish, preserve punctuation, brackets, and quote marks exactly.
- Ask before destructive commands or installing global packages.

## Working style

- Concise. No padded praise.
- Pause for review between major steps rather than doing everything at once.
- Flag copyright questions (e.g. how much NTV text can go on a public site) — don't guess.
