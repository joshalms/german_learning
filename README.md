# german_learning

Josh's personal learning app — a single-file vocabulary trainer (`index.html`, no build step, no dependencies). Open it in a browser or host it as a static page; all progress is stored in `localStorage`.

## Modules

- **German B2 trainer** — 2,307 words across 62 topic categories, learned in interleaved sessions (study → multiple choice → typed recall) and reviewed with SM-2 spaced repetition. Includes topic practice, weekly review, sentence practice, an activity chart, custom word import (CSV), and per-word editing.
- **French beginner module** — grammar lessons plus A1–A2 vocabulary with the same learn/review pipeline.

## Features

- **Manual override** — if a typed answer is marked wrong but was a valid alternative translation, click **“✓ My answer was actually correct”** to count it as correct (stats and the SRS mistake mark are reverted, and the normal rating buttons appear). Multiple-choice cards have an equivalent **“Mark as correct (misclick)”** link.
- **Dark mode** — follows the system preference; toggle manually with the 🌙/☀️ button on the home screen (persisted).
- **Keyboard shortcuts** — `Enter` submits and advances; `1`–`4` picks multiple-choice options and SRS ratings (Again/Hard/Good/Easy).
- **Word list search** — live filter in every word-list view.
- **Progress export/import** — JSON backup of both languages from the home screen.

## Word list

The German word list lives in `index.html` as `const WORDS=[...]` and is the source of truth for SRS progress (progress is keyed by word index, with schema migrations for historical reorders). Validate its integrity with:

```
node tools/validate-words.mjs
```

Checks: the list parses, every entry has non-empty `g`/`e`/`c` fields, and there are no exact duplicate German+English pairs. Repeated German headwords with different senses (e.g. *das Gericht* = dish vs. court) are intentional and allowed.
