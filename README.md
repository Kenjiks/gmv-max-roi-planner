This is Kenjiks's first git project!

## Product GMV Max · ROI Planner

`index.html` is a one-page interactive tool that runs in the browser. There is nothing to install, and all calculations happen on the user's device.

It helps TikTok Shop sellers running **Product GMV Max**:
- see their **true net profit** after TikTok Shop fees, COGS, affiliate commission, refunds, shipping and fixed costs
- find their **break-even ROI**
- find the **Growth ROI**: the lowest target ROI that keeps their minimum net profit margin (the most GMV inside their profit floor)
- find the **Profit-max ROI**
- compare scenarios, including **incremental ROI** and **worst-case profit** under the 90% ROI guarantee
- share a **link that keeps their inputs**, or print / save it as a PDF

### Scaling model
By default the tool uses TikTok GMV Max benchmark data (from a base target ROI of 3.6):

| Lower target ROI to | GMV uplift (up to) |
|---|---|
| 3.5 | +3% |
| 3.3 | +9% |
| 2.6 | +33% |

The curve is interpolated in log-log space and applied in proportion to the seller's current ROI. Values beyond 2.6/3.6 of current ROI are extrapolated. A "realisation %" setting scales the "up to" uplift. Users can also switch to a custom elasticity, optionally fitted from their own history.

### Profit maths
- Margin before ads `m = (1 − refund%) × (1 − fees% − COGS% − affiliate%) − (shipping + packaging) / AOV`
- Break-even ROI `= 1 / m`
- Net profit `= GMV × m − ad spend − fixed costs`, with ad spend `= GMV / ROI`
