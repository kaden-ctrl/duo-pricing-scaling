# Duo Price Book — proposal for management

A plan to replace ad-hoc, per-deal pricing with one published price book, a hard
margin floor, and a discount authority matrix — so pricing is repeatable and can
scale with headcount.

**Deliverable:** [`pricing-plan.html`](pricing-plan.html) — the document to present.

## The problem, in one line

Eight AiR engagements signed or proposed in 2026 carry six different prices
between $550 and $2,200/month for substantially overlapping scope, and none of
them reference a rate card. The rate card was last updated in June 2024 and no
longer describes what we sell.

## The five decisions requested

| # | Decision | Owner |
|---|---|---|
| D1 | Adopt three published AiR tiers at $1,200 / $1,500 / $2,500 per location | Lance |
| D2 | Adopt a hard gross-margin floor of 50%; list prices set to clear 60% | Lance |
| D3 | Stop bundling ad spend into the monthly fee; restore the 2024 campaign equation | Lance, Kaden |
| D4 | Tie included build work (websites, video) to a minimum term | Lance, Max |
| D5 | Retire the four undefined discount names; publish a discount authority matrix | Lance |

## The core finding

Every AiR dashboard costs Duo **$225/month** before anyone touches the account.
Against our own team-margin model (mid Digital Strategist at $5,500/month
carrying 8 accounts, 60% gross margin as the hire threshold):

```
accounts per rep needed = 5500 / (0.40 × price − 225)
```

| Price/mo | Accounts per rep for 60% GM |
|---:|---:|
| $550 | not achievable at any caseload |
| $650 | 158 |
| $750 | 74 |
| $1,200 | 22 |
| $1,500 | 15 |
| $2,500 | 8 |

At $550 the platform fee alone exceeds the entire 40% cost allowance. The
sub-$1,000 band cannot be delivered profitably at any volume, which is why the
proposal removes it rather than discounting into it.

## Proposed tiers

| Tier | List | Hard floor | Delivery cap | Caseload | Term |
|---|---:|---:|---:|---:|---|
| AiR Core | $1,200 | $1,000 | 5 hrs/mo | 20–22 | monthly |
| AiR Signal (default) | $1,500 | $1,200 | 8 hrs/mo | 14–15 | 6 months |
| AiR Complete | $2,500 | $1,850 | 16 hrs/mo | 8 | 12 months |

Floors are derived: each is the price at which that tier's platform cost plus
its delivery cap still leaves 50% gross margin.

Discounts reduce to two published programs — multi-location (15% second
location, 25% third+) and annual prepay (8%) — stacking to a maximum of 30%,
never below the tier floor.

## Live item

The CMP proposal's single-office tier bundles AiR *plus a full website* at
$1,500/month on a six-month term. Amortising the build across that term lands
the engagement near **36% gross margin**, below the 45% line our own model marks
as "cannot hire." The two- and three-office tiers hold up. The single-office
tier should be repriced or the website removed before it goes out.

## Open inputs

These sharpen the numbers but do not block the decisions:

1. **Current wage data** — the $5,500 figure and 8-account caseload come from the
   team-margin sheet last updated in 2023. Every floor moves if that has moved.
2. **Actual hours per account** — no time tracking against clients was found, so
   delivery caps are budgets rather than measurements.
3. **A complete MRR list** — this is built from the eight agreements locatable in
   Drive; a full list would size how much revenue currently sits below floor.

## Files

- `pricing-plan.html` — the presentation document
- `data/price-points-2026.csv` — the evidence table behind section 01

## Sources

Duo Pricing Sheet (June 2024) · Duo Team Margins & Utilisation Rates ·
Quarterly Goals 2025 · monthly budget sheets June–September 2026 · client
services agreements for Santiam Hospital & Clinics, Mill Forest Dental Group,
Kobico and CIS Office Furniture · Lawn Doctor 2026 options breakdown · CMP AiR
proposal.
