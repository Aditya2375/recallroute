# RecallRoute

Source-grounded revision cards and confidence signals. Education-track prototype built November 21, 2026 for STEM2Connect.

## Try it

- [Open the live app](https://aditya2375.github.io/recallroute/)
- [Watch the captioned v6.1 live demo](https://youtu.be/-suVm7Wh64o)
- [Download the modular source archive and tests](https://github.com/Aditya2375/recallroute/blob/main/4-recallroute-source.zip) using GitHub's download button.

To run locally:

1. Install Python 3, then run `python3 -m http.server 8080` in this folder.
2. Open `http://localhost:8080` in a browser.
3. Load the synthetic library example, or paste notes you have permission to use, one fact per line.
4. Make cards, attempt a blank, set confidence, then check the source.
5. Open **Reflect** to compare confidence with exact-match recall.
6. Download a session JSON to resume later. Refreshing clears the in-memory session.

No build step, API key, account or paid service. The modular development runtime files are `index.html`, `style.css`, `app.js`, `bg.js`, and `core.js`. The repository index.html is a self-contained version with embedded styles and code. The downloadable source archive contains the modular development version. Use a local HTTP server for that version. Current Chrome was tested; other modern browsers are not yet verified.

## What works

- Up to 40 extractive cloze cards from notes, with the original text and source-line evidence.
- Exact-match answer checking with case, whitespace and trailing-punctuation normalization.
- Confidence recorded before revealing answers.
- A transparent priority queue: misses first, high-confidence misses get extra priority, then unseen cards.
- A session dashboard with recall, average confidence and high-confidence misses.
- Downloadable JSON session and CSV attempts. JSON import validates fields and re-scores answers.
- An interactive practice route map: each card is a node on a drawn path, coloured by state and clickable to jump to that card.
- A dark entry stage with an original projected ribbon, travelling route markers, pointer-eased card depth and an interactive source-linked recall example. Separate entry actions focus the notes editor or start the synthetic example route. Motion has a pause control and respects prefers-reduced-motion.
- Animated confidence slider, count-up session signals and drawn bar charts; no animation library, all hand-written JavaScript.
- Responsive desktop/mobile layout, keyboard controls, labelled inputs and live feedback.
- Notes remain in the tab. There is no analytics, tracking, persistence or external API call in the app. The interface loads zero third-party resources: no fonts, scripts, styles or images from any external host.

The library example is invented, not a real event or factual reference.

## AI assistance and attribution

This prototype was developed with **Instinct, an AI assistant**. AI assistance produced the initial concept, implementation, interface text, styling, automated tests and this documentation, and helped run checks. This is an AI-assisted prototype, not a claim that Aditya personally wrote or tested every line. Any participant reflection about learning or personal contributions must come from the participant.

There is **no runtime AI model** in this version. Card extraction and priority scoring are deterministic rules. It does not claim to reason about the notes, understand a subject, or generate validated teaching material. The rules include a no-integrated-AI allowance tied to unavailable API credits. The participant confirmed on November 21, 2026 that he has no API credits. This deterministic prototype may not satisfy the event's AI requirement; judges decide eligibility and scoring.

No earlier flagship project, external dataset, paid service or third-party runtime library was used. The sample is original synthetic text. Development browser checks used Playwright, which is not bundled with the app. Unit tests use the Node.js test runner. Python's standard HTTP server is used for local preview.

## Tests

Unzip the source archive. With Node.js 20 or later:

```sh
npm test
```

Fifteen unit tests cover source-span traceability, input limits, answer normalization, priority ordering, empty metrics, confidence validation, import validation/re-scoring, formula-safe CSV, HTML-like text as data, blank-line numbering, 40-card caps and invalid timestamps. The app inserts user-supplied text through `textContent`, not `innerHTML`.

A local Chromium browser flow was checked for example-card generation, wrong and right answer feedback, route-map card jumping, confidence analytics, session export/clear/import, zero external network requests and a 390 px mobile layout. A separate 320 px edge flow exercises a 40-card route, keyboard grading, literal underscores, source-line gaps, reduced-motion controls and horizontal overflow. A computed-style text contrast regression passes all three views at 1440px and 320px; this is not a full accessibility audit. The landing keyboard reveal, 320px entry, editor focus action, example-route action and frozen canvas pixels while paused were checked separately. Desktop and mobile screenshots were visually inspected. These are development checks, not user trials or evidence of improved learning outcomes.

## Limits and next steps

- Cloze extraction may pick an unhelpful word. Review before using; manual card editing is a planned improvement.
- Exact matching can mark a correct paraphrase wrong. This prototype intentionally does not use an unverified semantic grader.
- Priority is a simple heuristic, not a validated spaced-repetition method.
- English-oriented extraction; multilingual support has not been tested.
- Only the first 40 eligible lines become cards. Long or very short lines are skipped.
- No real classroom trial, educator review, learning-outcome study, accessibility audit or cross-browser certification has been completed.
- No personal data should be pasted into a demo or shared session file. Exported files include notes and answers.
- Browser history, extensions and the host serving the app are outside its privacy guarantees.
- A deployment host can receive normal page requests even though note content is never sent by the application.

Next: manual card editing, better line selection, a screen-reader and cross-browser audit, and an opt-in educator review with synthetic material first.

## Project status

Working prototype, not a submitted hackathon entry by itself. Devpost description, demo and any personal reflection must be completed truthfully. The code is MIT licensed; see LICENSE.
