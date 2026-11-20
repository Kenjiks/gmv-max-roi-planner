# Product GMV Max · ROI Planner

## What this is
A one-page, client-facing calculator for TikTok Shop sellers running **Product GMV Max** (Malaysia market, currency RM by default). It shows a seller's true net profit after all costs and recommends a target ROI:
- **Break-even ROI** = 1 ÷ margin before ads
- **Growth ROI**: the lowest target ROI that keeps the seller's minimum net profit margin (the most GMV inside their profit floor)
- **Profit-max ROI**: the target ROI with the highest net profit

The owner is a TikTok Client Solutions Manager who is new to coding. Explain changes in plain language, avoid jargon, and say what they need to click on GitHub when something needs their action.

## Structure and deployment
- Everything is in **`index.html`**: plain HTML, CSS and JavaScript. No build step, no dependencies, no server. All calculations run in the browser.
- Live site: GitHub Pages from the **`main`** branch, root folder → https://kenjiks.github.io/gmv-max-roi-planner/
- To test locally, open `index.html` in a browser. Inputs are stored in the URL after `#` (shareable links), e.g. `index.html#cur=RM&gmv=100000&spend=27778&troi=3.6`.
- Before committing UI changes, render the page with Playwright (desktop ~1300px and mobile 390px), check for console errors, and look at a screenshot.

## Model (keep these decisions unless the owner changes them)
- Margin before ads `m = (1 − refund%) × (1 − fees% − COGS% − affiliate%) − shipping% − packaging per order ÷ AOV`
  - Shipping is a **% of GMV** (net of customer-paid shipping and platform subsidies). Packaging/other is an **amount per order**.
  - AOV = GMV ÷ number of orders (same period, excluding cancelled orders).
  - BPC (Beauty & Personal Care) TikTok Shop fee range: 14.58%–20.52%. The fee input links to the TikTok Shop MY commission page.
- **Other shop GMV** (organic and other channels) counts toward profit but does **not** scale with target ROI. Only GMV Max GMV scales.
- **How GMV responds to target ROI** (section 4), set by two inputs:
  - "Lower target ROI by 10% → GMV rises by" **default 10.7%**. Source: TikTok benchmark campaign at base ROI 3.6 (→3.5 up to +3%, →3.3 up to +9%, →2.6 up to +33%). The benchmark curve's shape (piecewise linear in log-log space) is kept and scaled to the user's figure, so the default reproduces +3/+9/+33% exactly.
  - "Raise target ROI by 10% → GMV falls by" **default 11.7%**. Source: 168 weekly observations (Jun–Nov 2026) of target ROI and ad spend across 7 TikTok Shop accounts. In weeks above a shop's usual ROI, spend fell about 2.3% per 1% higher target (spend ∝ ROI^−2.3, so GMV ∝ ROI^−1.3). The average across all weeks was 1.7 (95% CI 1.4–2.0).
  - Spend = GMV Max GMV ÷ ROI (adjusted by the delivered-vs-target ROI ratio).
  - Data range: about 0.72× to 1.2× of the current target ROI. Outside it, results are extrapolated: table rows are faded and profit-max is labelled "(estimate)".
- Optional **budget cap**: spend can't exceed it, and Growth ROI never goes below the ROI where the budget runs out.
- **Worst-case profit** assumes delivery at 90% of target ROI (the GMV Max ROI guarantee credits any shortfall below 90%).
- An advanced box lets CSMs paste a shop's target ROI / spend history to estimate the "raise" figure.

## Rules
- **Never commit client data** (shop names, P&Ls, client BI exports) or raw internal datasets. Only aggregate figures, like the defaults above, belong in the repo. Client scenarios are shared via `#` links, not stored.
- Keep the **bilingual disclaimer banner** (English + Malay) at the top, including on print.
- Keep `<meta name="robots" content="noindex, nofollow">` so search engines don't list the page.
- Keep the tool honest: show when a recommendation reduces profit, flag extrapolation, and don't overstate the benchmark ("up to").
- Charts: one y-axis only, colour-blind-safe palette, hover tooltips, light and dark mode.
- Scope is **Product GMV Max** only. Live GMV Max is out of scope unless the owner asks.

## Workflow
- Work on a feature branch, then open a pull request into `main`. The owner reviews and merges. Merging to `main` updates the live site within a couple of minutes.
- Don't put model names or AI identifiers in commits, code comments or the page.
