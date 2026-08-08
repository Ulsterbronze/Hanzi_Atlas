# 汉字 Atlas — Frequency Flashcards

A single-file, offline-first Chinese vocabulary app: 1,500 hanzi and 3,000 words, ranked by real corpus frequency, each broken down into its component pieces to help build mnemonics. Installable as a standalone app (PWA) — no framework, no build step, no backend.

## Features

- **1,500 hanzi + 3,000 words**, ranked by real frequency data (see *Data sources* below)
- **Component breakdowns** on every card — see the building blocks before you flip to pinyin/meaning
- **100 radicals + 86 phonetic components** as their own reference cards
- **Weighted or true-random shuffle**, toggleable — weighted mode biases toward higher-frequency cards using real corpus-derived weights (hanzi) or a modeled Zipf curve (words)
- **Dual-range rank sliders** — study a specific frequency band (e.g. ranks 200–500) instead of everything at once
- **Multi-select type filters** — combine Hanzi + Words (or any mix) in one shuffle pool
- **Text-to-speech** pronunciation on every card (Web Speech API)
- **Browse view** with search, and per-card view counts shown right on the card
- **View-count color tiers in Browse** — a card's border/badge color shifts through 7 stages as its view count climbs (red → yellow → green → blue → bronze → silver → gold), with thresholds loosely informed by vocabulary-acquisition research rather than picked arbitrarily: 1–2 / 3–5 / 6–7 / 8–13 / 14–20 / 21–35 / 36+. (This tracks raw view count, not spaced-repetition intervals, so treat it as a familiarity milestone rather than a precise mastery measure.)
- **Progress tracking**, stored locally on your device:
  - All-time unique hanzi/word coverage
  - Daily history (last 14 days shown, up to 365 kept)
  - Per-card view counts, visible in Browse
- **Installable PWA** — add to home screen, opens standalone (no browser UI), works fully offline after first load

## Data sources

- **Hanzi frequency, rank, pinyin, stroke count, radical, HSK level:** [Jun Da's Modern Chinese Character Frequency List](http://lingua.mtsu.edu/chinese-computing/statistics/) (ranks 1–500 from the original curated set; 501–1000 and 1001–1500 added later from the same source) and hanziDB
- **Hanzi component decomposition:** [Make Me a Hanzi](https://github.com/skishore/makemeahanzi), cross-checked against real stroke counts — a component set is only shown if its strokes actually sum to the character's true stroke count
- **Word frequency (ranks 1001–3000):** [jieba](https://github.com/fxsjy/jieba)'s corpus-derived frequency dictionary
- **Word/component definitions:** [CC-CEDICT](https://cc-cedict.org/)
- **Kangxi radicals:** the standard 214-radical table, with traditional radical meanings (not modern standalone character meanings — e.g. 厂 is glossed "cliff," not "factory")

Where the underlying data didn't support something reliably (e.g. no raw frequency counts exist for words, so word weighting is a modeled approximation, not measured), that's noted in-app rather than presented as more precise than it is.

## Installing on your phone

1. Host this folder somewhere static and public — [GitHub Pages](https://pages.github.com/) works well and is free. In this repo: **Settings → Pages → Source: "Deploy from a branch" → Branch: `main`, folder `/ (root)` → Save**.
2. Open the resulting URL in Chrome (or another Chromium-based browser) on your phone.
3. Tap **⋮ → Install app** (wording may vary: "Add to Home screen").
4. Launch it from your home screen from then on — no browser needed.

## Updating

Whenever a file changes, re-upload it to the repo root, overwriting the old version. **If `sw.js` changed, it must be re-uploaded too** — the service worker only checks for updates when its own file changes, so shipping a new `index.html` without a new `sw.js` will keep serving the old cached version indefinitely. After updating, fully close and reopen the installed app so the new service worker takes over.

Your progress (all-time stats, daily history, per-card view counts) lives in your browser's local storage, tied to this installed app — it's untouched by file updates, but isn't backed up anywhere and will be lost if you uninstall the app or clear its site data.

## Structure

```
index.html              the app itself
manifest.json            PWA manifest (name, icons, display mode)
sw.js                    service worker (offline caching)
icon-192.png              app icon
icon-512.png              app icon
icon-maskable-512.png     Android adaptive icon variant
```

All files must stay together with these exact names for install/offline support to work.
