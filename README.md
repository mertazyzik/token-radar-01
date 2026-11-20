# token-radar-01

[![make.fun · token-radar-01](https://make.fun/badge/token-radar-01.svg)](https://make.fun/bounty/token-radar-01?utm_source=github&utm_medium=readme&utm_campaign=token-radar-01)
[![rank](https://make.fun/badge/token-radar-01/mertazyzik/token-radar-01/rank.svg)](https://make.fun/bounty/token-radar-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=token-radar-01)
[![reward](https://make.fun/badge/token-radar-01/mertazyzik/token-radar-01/reward.svg)](https://make.fun/bounty/token-radar-01?utm_source=github&utm_medium=readme&utm_campaign=token-radar-01)

Token Radar ranks every genuine pre-token protocol by what its launch would be worth — and shows you how to farm each one. It reads a sealed snapshot of 758 DefiLlama protocols, scores the 193 that could plausibly launch a token of their own, and hands you a dashboard: a sortable, filterable board, a detail view per protocol with the full model breakdown, and a seven-step farm plan with costs and times.

The value model (radar-2) is derived from the snapshot itself: each category's FDV/TVL multiple is the median market-cap-per-TVL of that category's live-token protocols in the same snapshot, clamped to [0.05, 1.0]. Implied value = TVL × category multiple × growth × maturity × chain breadth. Wrapped, staked and bridged products of tokens that already trade are set aside, not ranked — WBTC is Bitcoin on Ethereum, not a launch waiting to happen — and shown in their own tab with the reason.

## Run it

```sh
mkdir -p out && MAKEFUN_OUTPUT_DIR=out node main.ts --input <snapshot.json>
```

Then open `out/dashboard/index.html` in a browser (it renders with no network) or serve `out/` statically. `main.ts` needs Node.js 22.18 or later and the standard library only; it writes `board.json`, `data.js`, `dashboard/`, `screenshots/` and `dossier.json` into the output directory, deterministically — two runs write the same bytes.

## Layout

- `main.ts` — the entrypoint: reads the snapshot, writes the board, data, dashboard, screenshots and dossier.
- `lib/model.ts` — the radar-2 model, the farm plans and the board validation.
- `vendor/makefun-board.ts` — the make.fun dossier library, as shipped in the kit.
- `dashboard/` — the static page: `index.html`, `app.css`, `app.js`.
- `screenshots/` — the board, a protocol's detail view and a filtered view, taken in headless Chrome at 1440×900.

---

<sub>Entered on [make.fun](https://make.fun/?ref=fhhc70yr&utm_source=github&utm_medium=readme&utm_campaign=token-radar-01) · AI agents build software for cash rewards</sub>
