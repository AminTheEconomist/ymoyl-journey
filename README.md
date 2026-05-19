# YMOYL Journey

A self-paced web companion for *Your Money or Your Life* (Vicki Robin & Joe Dominguez) — track where you are across the **four FIs**: Financial Intelligence → Integrity → Independence → Freedom.

**Live site:** [`ymoyl-journey.vercel.app`](https://ymoyl-journey.vercel.app/)

## What it is

A single-page, client-side dashboard:

- 4 FIs roadmap with per-step progress
- 5-year wall chart (income vs. expense)
- Top spending categories
- **Hours-of-life-energy** unit toggle (the YMOYL move — everything in hours instead of dollars once you've entered your real hourly wage)
- **FIRE flavor selector** — Lean / Regular / Fat / Coast / Barista
- **What-if scenario sandbox** — drag a slider, watch years-to-FI move
- **Years until crossover** as the hero number
- Anomaly flagging (months where spending behaves weirdly)
- URL-namespaced profiles — share the link, each person gets their own data
- No login, no backend. Data lives in your browser's localStorage.

## Profiles

Just append `?p=YOURNAME` to the URL.

- `https://ymoyl-journey.vercel.app/?p=amin`
- `https://ymoyl-journey.vercel.app/?p=sara`

Each profile is independent. The same browser holds all profiles; they don't see each other's data.

## Privacy

Everything is client-side. No analytics, no tracking, no server-side storage. Clear your browser data → everything is gone. Want it on another device? Set the same profile name and re-enter values. (Encrypted cloud sync is on the roadmap as an opt-in.)

## Architecture

Three layers, all toggleable:

1. **Modes** (presentations of the data — pick at onboarding):
   - Solo Dashboard *(default — implemented)*
   - Values-Led *(planned)*
   - Household *(planned)*

2. **Toggleable features** (header controls):
   - Unit: dollars / hours of life energy ✅
   - FIRE flavor: Lean / Regular / Fat / Coast / Barista ✅
   - Real-time what-if sliders ✅
   - Tombstone framing *(planned)*
   - Decade canvas *(planned)*
   - Hexagonal roadmap variant *(planned)*

3. **Opt-in services** (require setup):
   - CSV drag-and-drop import *(planned)*
   - Weekly coach via cron *(planned)*
   - Git audit trail *(planned)*
   - Encrypted cloud sync *(planned)*

## Roadmap

- [x] v2.0 — Vercel deployment, profile namespacing, hours/dollars toggle, FIRE flavors, what-if sliders
- [ ] v3 — Mode picker (Solo / Values-Led / Household) + Monte Carlo cone + entry quiz
- [ ] v4 — Hexagonal roadmap, decade canvas, identity badge, tombstone toggle
- [ ] v5 — CSV import, git audit trail, weekly coach
- [ ] v6 — Opt-in encrypted cloud sync (only if needed)

## Development

It's one HTML file. No build step.

```bash
open index.html
```

Data is embedded at the top of the `<script>` block as a JS const. To refresh from the workbook, run the extractor at `/tmp/extract_data.py` (see workbook at `~/Documents/Finance/YMOYL/YMOYL_Workbook.xlsx`) and inline the new JSON.

## Inspired by

- *Your Money or Your Life* — Vicki Robin & Joe Dominguez
- [WalletBurst FIRE calculator](https://walletburst.com/tools/fire-calculator/) — the interactive-slider pattern
- [Wealthfolio](https://wealthfolio.app/) — local-first, open-source philosophy
- [Dave Ramsey's Baby Steps](https://www.ramseysolutions.com/dave-ramsey-7-baby-steps) — linear gamified progression
- [Mr. Money Mustache · Shockingly Simple Math](https://www.mrmoneymustache.com/2012/01/13/the-shockingly-simple-math-behind-early-retirement/) — savings-rate-to-years-to-FI insight
