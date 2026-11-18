This is Kenjiks's first git project!

## GMV Max ROI Sweet-Spot Calculator

`gmv-max-optimizer.html` is a single-file tool you open in a browser. It needs no installs.

It helps TikTok Shop sellers:
- work out their **true net profit** from GMV, ad spend, COGS, platform fees, affiliate commission, refunds, shipping and fixed costs
- find their **break-even ROI** (the ROI below which ads lose money)
- find the **sweet-spot ROI**, the target ROI that maximises net profit
- see the **most GMV they can reach while keeping today's profit** by lowering the target ROI
- check the **worst-case profit** under GMV Max's 90% ROI guarantee

### Model
- Contribution margin `m = (1 − refund%) × (1 − COGS% − fees% − affiliate%) − (shipping + packaging) / AOV`
- Break-even ROI `= 1 / m`
- Scaling: `GMV(ROI) = GMV_now × (ROI_now / ROI)^e`, where `e` is the scaling elasticity (set by hand or fitted from past periods)
- Sweet-spot ROI `= break-even ROI × (1 + 1/e)`
