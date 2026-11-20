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

### Delivery model (how spend responds to target ROI)
GMV Max spend follows `spend ∝ ROI^(−k)` and `GMV = ROI × spend`. A higher target ROI makes spending harder, so GMV falls. A lower target makes spending easier, so GMV rises, but each extra RM 1 of spend returns less.
- **Raising ROI**: spend drop factor `k = 2.3` by default. This comes from 168 weeks (Jun–Nov 2026) of target ROI and spend across 7 shops, using weeks above each shop's usual ROI. The average across all weeks was 1.7 (95% range 1.4–2.0).
- **Lowering ROI**: the benchmark uplift table (below) or a spend gain factor (the benchmark implies about 1.9–2.0).
- **Budget cap** (optional): spend never goes above it, and Growth ROI never goes below the ROI where the budget runs out.
- Users can paste their own target ROI / spend history to fit `k` for their shop.
- Profit-max ROI is only searched inside the data range (about 0.84×–1.2× the current ROI).

### Benchmark uplift (lowering ROI)
By default the tool uses TikTok GMV Max benchmark data (from a base target ROI of 3.6):

| Lower target ROI to | GMV uplift (up to) |
|---|---|
| 3.5 | +3% |
| 3.3 | +9% |
| 2.6 | +33% |

Users can edit the uplift points to match their own campaign. The curve is interpolated in log-log space and applied in proportion to the seller's current ROI. Values beyond 2.6/3.6 of current ROI are extrapolated. A "realisation %" setting scales the "up to" uplift. Users can also switch to a custom elasticity, optionally fitted from their own history.

### Profit maths
- Margin before ads `m = (1 − refund%) × (1 − fees% − COGS% − affiliate%) − (shipping + packaging) / AOV`
- Break-even ROI `= 1 / m`
- Net profit `= GMV × m − ad spend − fixed costs`, with ad spend `= GMV / ROI`
