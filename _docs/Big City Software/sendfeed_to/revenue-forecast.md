# sendfeed.to — Revenue Forecast (Year 1)

*Prepared April 2026. Assumes a May 2026 launch.*

---

## Assumptions

All projections are driven by five inputs. Adjust these and the numbers follow.

| Input | Conservative | Base | Optimistic |
|---|---|---|---|
| New customers in month 1 | 5 | 10 | 20 |
| New customer growth (per month) | +1/month | +2/month | +3/month |
| Monthly churn rate | 6% | 4% | 3% |
| ARPU | $9 | $11 | $13 |
| Add-on revenue (subscriber overages) | Negligible | ~$0.50/customer | ~$1/customer |

**ARPU is derived from tier distribution:**

| Tier | Price | Conservative | Base | Optimistic |
|---|---|---|---|---|
| Starter | $6/mo | 65% | 55% | 45% |
| Growth | $14/mo | 28% | 35% | 40% |
| Pro | $29/mo | 7% | 10% | 15% |
| **Blended ARPU** | | **~$9** | **~$11** | **~$13** |

**On churn:** 4% monthly churn (~40% annual) is realistic for early-stage consumer SaaS with no marketing budget and cold traffic. As the product matures and word-of-mouth improves, this should drop. Pro users tend to churn less than Starter users.

---

## 12-Month MRR Projection

### Base Scenario

| Month | New Customers | Total Customers | MRR |
|---|---|---|---|
| May 2026 | 10 | 10 | $110 |
| Jun 2026 | 12 | 22 | $242 |
| Jul 2026 | 14 | 35 | $385 |
| Aug 2026 | 16 | 50 | $550 |
| Sep 2026 | 18 | 66 | $726 |
| Oct 2026 | 20 | 83 | $913 |
| Nov 2026 | 22 | 102 | $1,122 |
| Dec 2026 | 24 | 122 | $1,342 |
| Jan 2027 | 26 | 143 | $1,573 |
| Feb 2027 | 28 | 165 | $1,815 |
| Mar 2027 | 30 | 188 | $2,068 |
| Apr 2027 | 32 | 212 | $2,332 |

**Year 1 total revenue: ~$13,200**
**ARR at end of Year 1: ~$28,000**

---

### Conservative Scenario

| Month | New Customers | Total Customers | MRR |
|---|---|---|---|
| May 2026 | 5 | 5 | $45 |
| Jun 2026 | 6 | 11 | $99 |
| Jul 2026 | 7 | 17 | $153 |
| Aug 2026 | 8 | 24 | $216 |
| Sep 2026 | 9 | 32 | $288 |
| Oct 2026 | 10 | 40 | $360 |
| Nov 2026 | 11 | 49 | $441 |
| Dec 2026 | 12 | 58 | $522 |
| Jan 2027 | 13 | 68 | $612 |
| Feb 2027 | 14 | 78 | $702 |
| Mar 2027 | 15 | 88 | $792 |
| Apr 2027 | 16 | 99 | $891 |

**Year 1 total revenue: ~$5,100**
**ARR at end of Year 1: ~$10,700**

---

### Optimistic Scenario

| Month | New Customers | Total Customers | MRR |
|---|---|---|---|
| May 2026 | 20 | 20 | $260 |
| Jun 2026 | 23 | 42 | $546 |
| Jul 2026 | 26 | 67 | $871 |
| Aug 2026 | 29 | 94 | $1,222 |
| Sep 2026 | 32 | 123 | $1,599 |
| Oct 2026 | 35 | 154 | $2,002 |
| Nov 2026 | 38 | 187 | $2,431 |
| Dec 2026 | 41 | 222 | $2,886 |
| Jan 2027 | 44 | 259 | $3,367 |
| Feb 2027 | 47 | 298 | $3,874 |
| Mar 2027 | 50 | 339 | $4,407 |
| Apr 2027 | 53 | 382 | $4,966 |

**Year 1 total revenue: ~$28,400**
**ARR at end of Year 1: ~$59,600**

---

## Summary

| Scenario | Year 1 Revenue | ARR at EOY1 | Customers at EOY1 |
|---|---|---|---|
| Conservative | $5,100 | $10,700 | ~100 |
| Base | $13,200 | $28,000 | ~210 |
| Optimistic | $28,400 | $59,600 | ~380 |

---

## What Moves the Needle Most

**Churn is the most dangerous lever.** At 6% monthly churn, you're replacing 50%+ of your customer base every year. Every product improvement that makes the product stickier (digest preview, subscriber growth tracking, reliability) compounds faster than any acquisition effort. Get churn below 3% and the base scenario looks like the optimistic one.

**Tier distribution matters more than volume at small scale.** The difference between a Starter-heavy ($9 ARPU) and Growth-heavy ($13 ARPU) mix is ~45% more revenue from the same number of customers. The onboarding flow should guide serious users toward Growth — it's the right tier for anyone with an active publishing cadence.

**Acquisition at this stage is mostly about finding the right channel.** The base scenario needs ~10–30 new signups per month — a realistic goal for a focused effort in developer communities, Indie Hackers, Hacker News, and the Statamic/Laravel ecosystem. That's not paid ads territory; it's showing up in the right places.

**Add-on revenue ($1/1,000 subscribers) is small but compounding.** Users who hit their subscriber limit and pay for overages rather than churning are a strong signal. Track this rate — high overage revenue means the product is working and the user is growing.

---

## Honest Caveats

- These numbers assume May 2026 launch. Every month of delay shifts the entire curve right.
- Acquisition assumptions are not grounded in a specific channel or marketing plan — they reflect what's plausible for a solo founder with a niche but clear product. Actual numbers could be higher or lower by an order of magnitude.
- No infrastructure or tooling costs are modelled here (hosting, transactional email for auth/confirmations, Stripe fees ~2.9%+$0.30). At this scale, costs are low — likely under $100/month to start.
- The free trial (14 days, card required) means some signups won't convert. A reasonable trial-to-paid conversion of 40–60% is baked into the "new customers" figures above — not gross signups.
