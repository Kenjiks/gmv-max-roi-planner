This is Kenjiks's first git project!

## Product GMV Max · ROI Planner

`index.html` is a one-page interactive tool that runs in the browser. There is nothing to install, and all calculations happen on the user's device.

It helps TikTok Shop sellers running **Product GMV Max**:
- see their **true net profit** (GMV Max GMV plus optional other shop GMV, which does not scale with ROI) after TikTok Shop fees, COGS, affiliate commission, refunds, shipping and fixed costs
- find their **break-even ROI**
- find the **Growth ROI**: the lowest target ROI that keeps their minimum net profit margin (the most GMV inside their profit floor)
- find the **Profit-max ROI**
- compare scenarios, including **incremental ROI** and **worst-case profit** under the 90% ROI guarantee
- share a **link that keeps their inputs**, or print / save it as a PDF

### How GMV responds to target ROI
Users answer two plain questions (defaults shown):
- **Lower target ROI by 10% → GMV rises by +10.7%.** This comes from a TikTok benchmark campaign (3.6→3.5 up to +3%, →3.3 up to +9%, →2.6 up to +33%). The tool keeps the benchmark curve's shape, where each further cut adds less, and scales it to the figure entered.
- **Raise target ROI by 10% → GMV falls by 11.7%.** This comes from 168 weeks (Jun–Nov 2026) of target ROI and spend across 7 shops: in weeks above a shop's usual ROI, spend fell about 2.3% per 1% higher target.

Spend = GMV ÷ ROI, so profit peaks at some ROI and then falls as delivery dries up. Results outside the data range (about −28% to +20% of current ROI) are shown faded as estimates. There's an optional budget cap, and an advanced box to estimate the "raise" figure from a shop's own ROI/spend history.

### Profit maths
- Margin before ads `m = (1 − refund%) × (1 − fees% − COGS% − affiliate%) − shipping% − packaging per order / AOV`
- Break-even ROI `= 1 / m`
- Net profit `= GMV × m − ad spend − fixed costs`, with ad spend `= GMV / ROI`
