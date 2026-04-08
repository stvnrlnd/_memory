# tokidoki.pro — Revenue Forecast

## Operations Cost Estimate

Infrastructure costs are low for a Laravel application at early scale:

| Item | Monthly Cost |
|---|---|
| VPS (Hetzner/DigitalOcean, 4GB RAM) | $20–40 |
| Managed database (or co-located early on) | $0–25 |
| Transactional email (Postmark/SES) | ~$10 |
| Backups, monitoring, misc | ~$10–20 |
| **Total** | **$50–100/month** |

Costs scale gradually with usage. A single paying Team customer covers operations from day one.

## Pricing Reference

| Tier | Monthly | Annual (monthly equiv.) |
|---|---|---|
| Free | $0 | — |
| Team | $99 | $79 |
| Business | $199 | $159 |

## Break-Even

| Scenario | Monthly Revenue | Covers Ops? |
|---|---|---|
| 1 Team customer | $99 | Yes |
| 2 Team customers | $198 | Yes (2x) |

Break-even requires a single paying customer. This is an unusually low bar for a SaaS product.

## Revenue Scenarios

Assumes a mix of monthly and annual customers, and a realistic free-to-paid conversion rate of 3–5% for B2B SaaS.

### Conservative (all Team, monthly billing)

| Customers | MRR | ARR |
|---|---|---|
| 10 | $990 | ~$12k |
| 25 | $2,475 | ~$30k |
| 50 | $4,950 | ~$59k |
| 100 | $9,900 | ~$119k |

### Realistic mix (Team + Business, ~20% annual)

| Team | Business | MRR | ARR |
|---|---|---|---|
| 25 | 5 | $3,470 | ~$42k |
| 50 | 10 | $6,940 | ~$83k |
| 100 | 20 | $13,880 | ~$167k |

### Upside (strong Business tier adoption)

| Team | Business | MRR | ARR |
|---|---|---|---|
| 50 | 25 | $9,925 | ~$119k |
| 100 | 50 | $19,850 | ~$238k |

## Pricing Competitiveness

At $99/month flat, tokidoki.pro competes favorably against per-seat tools for teams of 10+:

| Team size | ninety.io (~$9/user/mo) | tokidoki.pro (Team) |
|---|---|---|
| 5 users | $45 | $99 |
| 10 users | $90 | $99 |
| 15 users | $135 | $99 |
| 20 users | $180 | $99 |

The flat fee becomes a clear win at ~10 users. For teams under 10, the value differentiation (meeting intelligence, no EOS required) carries the price gap.

## Key Assumptions & Risks

- **Acquisition is the primary risk** — the unit economics work easily at modest scale; getting the first 10–25 paying customers is the hard part.
- **Free tier conversion** — the free tier must expose enough of the core value (meeting generation) to drive upgrades. Overly limiting the free tier kills conversion; too generous removes urgency to upgrade.
- **Annual plan mix** — higher annual adoption significantly smooths revenue and improves cash flow. Incentivizing annual at launch (prominent placement, clear savings) is worth prioritizing.
- **ninety.io pricing unverified** — competitive pricing above is based on an estimate. Should be confirmed before launch.

## Notes

- These projections are illustrative, not targets. Actual revenue depends entirely on acquisition strategy and product-market fit validation.
- A single design partner (e.g. ABHP) converting to a paid customer provides both revenue and a reference — disproportionately valuable at this stage.
