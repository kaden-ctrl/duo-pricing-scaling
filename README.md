# Duo Service Builder

An à la carte service menu. Pick services, and the bundle discount grows as
more are added.

**Deliverable:** [`service-builder.html`](service-builder.html)

## How it works

| Monthly services selected | Discount |
|---:|---:|
| 1 | none |
| 2 | 5% |
| 3 | 8% |
| 4 | 12% |
| 5+ | 15% |

Annual prepay (paid upfront) adds 10%. Combined discount is capped at 25%.

- The count uses **distinct monthly services**. Quantities inside one service
  (three social platforms, two locations) don't raise the tier. The whole AiR
  programme counts as one. Each ad channel counts separately, so a client
  running all four ad channels plus one other service reaches the top bundle
  tier on five line items.
- **One-time build work is never discounted**: the website build and video
  production stay at list.
- **Paid media is priced as a share of ad spend** (see below). The monthly
  total is management fee **plus** the ad spend itself, but the spend is a
  pass-through at cost and is never discounted. Only the fee Duo earns takes
  the bundle and prepay discounts.
- Minimum term derives from the selection: 12 months where a build or video is
  included, 6 months with the AiR programme, otherwise month to month.

## Paid media management

The management fee is a percentage of monthly ad spend rather than a flat
per-account retainer. The more a client spends, the lower the rate.

| Monthly ad spend | Management |
|---|---:|
| Under $2,000 | 50% |
| $2,000 to $4,999 | 40% |
| $5,000 to $9,999 | 35% |
| $10,000 to $24,999 | 32% |
| $25,000 and up | 30% |

Minimum management fee is **$1,000 a month**, which is what carries the bottom
band: $1,000 of spend costs $1,000 to manage, and 50% doesn't start biting
until $2,000.

Ad spend is added into the monthly total alongside the fee, so the headline
number is what the client actually pays each month. The panel breaks it out:

```
Monthly at list          $7,400     services + management fee
Bundle discount 15%     −$1,110     applies to the fee, not the spend
Ad spend (pass-through)  +$6,000     at cost, never discounted
Per month               $12,290     of which $6,290 is revenue to Duo
```

Two properties worth knowing before quoting it:

- The rate applies to the **whole spend**, not marginally. Crossing a tier
  lowers the fee outright: $4,999 of spend costs $2,000 to manage, $5,000
  costs $1,750. That's deliberate: it pays the client to move up.
- The fee **is** subject to the bundle and annual-prepay discounts, same as
  any other monthly service. The spend is not. Discounting a pass-through
  would come straight out of margin.

Paid media is four separate line items: Google Ads, Meta Ads, LinkedIn Ads and
TikTok Ads. Each carries its own monthly ad spend, but **the rate is set by
combined spend across every channel selected**, then applied to each channel's
own spend. Splitting $10,000 across four channels therefore costs the same to
manage as putting it all in one; charging each channel its own tier would have
penalised the client for diversifying.

The $1,000 minimum also applies once across paid media as a whole, not per
channel, so four channels do not stack four minimums. Where the minimum is what
is binding rather than the percentage, the row says "minimum fee" instead of
quoting an effective rate that would read alarmingly high (the floor on $1,500
of spend is 67%).

`data/paid-media-tiers.csv` holds the ladder with the fee at each band edge.

## Catalog

11 services across five categories: AI Search Visibility (AiR), Social Media,
Paid Media, Content & Creative, and Web & Search. Each carries a "What's
included" breakdown. Four presets (Local Presence, AI Visibility, Full Growth,
New Launch) pre-fill common combinations.

**AI Search Visibility is a single line**: AiR Dashboard and AEO Management,
$1,600 per location per month, six-month minimum. It folds in what used to be
four separate items: the dashboard and tracking ($1,200/location), Signal
Sessions ($400/mo), the baseline AI Visibility Audit (was $1,500 one-time) and
Multi-Location Reporting (was $350/mo). The audit and the roll-up are now
included rather than billed.

**Video Production is scoped by hours** rather than sold at a flat $4,000. It
runs $100 an hour with a 20-hour floor and a 500-hour ceiling, so $2,000 to
$50,000. The $100 rate is the old flat price divided by the 40 delivery hours
recorded for it, so a 40-hour job still prices at $4,000.

Retired from the menu: Short-Form Video, Content Capture Day, SEO, Call
Tracking & Attribution, ADA Compliance Monitoring, LinkedIn Job Posting,
Retargeting & Dark Posts, Blog Content, the Design Retainer and the Landing
Page Build. Website Management & Hosting moved from $350 to $100 a month.

Selections persist per browser via `localStorage`.

## Branding

From the Brand Guidelines doc (Duo Group entry):

- Blue `#019ED0`, white `#FEFEFE`, black `#000000`
- Typeface **Avenir Next LT Pro**, with Mulish substituting where it isn't installed
- AiR purple `#9A76D6` marks the AI Search Visibility line

### Adding the real logo

The page currently type-sets the wordmark. To use the actual artwork, open
`service-builder.html`, find the `var LOGO = "";` line near the top of the
script, and paste in a base64 data URI:

```
base64 -w0 Duo-Marketing-Group-Logo-2020-373px.png
```

Then `var LOGO = "data:image/png;base64,<paste>";`

The artwork has to be inlined, the artifact sandbox blocks external image
URLs. The source file is in Drive under Client logos / Duo Group, or as
`DUOGroupLogos.pdf`.

## Where the prices came from

`duogroup.com` is blocked by this environment's network egress proxy, so the
catalog was assembled from what Duo actually contracts and invoices:

- Duo Pricing Sheet (June 2024)
- AiR client agreements (Kobico, CIS Office Furniture, Mill Forest Dental)
- Santiam Hospital & Clinics services agreement
- Lawn Doctor 2026 options breakdown
- Monthly budget sheets, June to September 2026

**Email Marketing** is a reconstruction rather than a quoted figure and should
be confirmed. The 2024 card lists email at "$3,000/month," which reads as an
all-in program price and conflicts with the $200-per-extra-blast rate in the
Santiam agreement.

Four more figures are constructions and are not traceable to a signed
agreement. They are pricing decisions, not sourced rates:

- The **$1,600 AiR Dashboard and AEO Management** price is the two monthly
  components added together ($1,200 + $400). Bundling the audit and the roll-up in gives away
  $1,500 of one-time revenue and $350/mo on multi-location accounts.
- The **paid media tier ladder** is new. It was built to two anchors: $1,000
  of spend costs $1,000 to manage, $5,000 of spend is managed at 35%, with
  the rate starting at 50% and bottoming out at 30%.
- Against the old flat fee, the tiers cut revenue on small single-channel
  accounts (a $2,000 Meta-only client goes from $1,500 to $1,000) and on
  multi-channel accounts (three channels was $4,500 flat; $15,000 of combined
  spend is now $4,800, and $6,000 is $2,100). Worth checking against the
  delivery hours in `data/service-catalog.csv` before it goes to clients.
- The **$100/hr video rate** is the retired $4,000 flat price divided by the 40
  delivery hours recorded against it. The $2,000 floor and $50,000 ceiling are
  scoping decisions, not quoted jobs.

`data/service-catalog.csv` records every line with its source.

## Files

- `service-builder.html`: the menu
- `data/service-catalog.csv`: catalog with sources
- `data/paid-media-tiers.csv`: the ad-spend ladder
- `data/price-points-2026.csv`, `data/unit-costs-2026.csv`: reference data
- `archive/pricing-plan.html`: earlier pricing-rationale document, retired
