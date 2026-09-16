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

Management is priced **in bands on combined ad spend**, like tax brackets.
Each band applies only to the part of the spend that falls inside it, never to
the whole amount.

| Part of combined monthly spend | Rate on that part |
|---|---:|
| First $2,000 | 50% |
| $2,000 to $5,000 | 40% |
| $5,000 to $10,000 | 35% |
| $10,000 to $25,000 | 32% |
| Above $25,000 | 30% |

Minimum management fee is **$1,000 a month**, which carries everything below
$2,000 of spend.

Two properties follow from banding, and both are the point:

- **The fee always rises with spend.** Every extra dollar of spend adds fee at
  its band's rate, so there is no spend level where spending more costs less to
  manage. More spend means more work, and the fee reflects it.
- **The overall rate always falls.** Each new dollar is charged at a lower rate
  than the one before it. That is the volume discount.

A whole-spend tier table cannot do both at once, which is why this replaced
one. Dropping the rate on the *entire* amount at a threshold makes the fee fall
as spend rises: under the old table $4,999 of spend cost $2,000 to manage and
$5,000 cost $1,750.

What it works out to:

| Combined ad spend | Management | Overall rate |
|---:|---:|---:|
| $1,000 | $1,000 | minimum |
| $2,000 | $1,000 | 50% |
| $5,000 | $2,200 | 44% |
| $10,000 | $3,950 | 40% |
| $25,000 | $8,750 | 35% |
| $50,000 | $16,250 | 33% |

Ad spend is added into the monthly total alongside the fee, so the headline
number is what the client actually pays each month. The panel breaks it out:

```
Monthly at list          $7,000     services + management fee
Bundle discount 15%     −$1,050     applies to the fee, not the spend
Ad spend (pass-through)  +$6,000     at cost, never discounted
Per month               $11,950     of which $5,950 is revenue to Duo
```

(That is the Full Growth preset: $6,000 of combined ad spend across Google and
Meta, managed at 43% overall.)

The fee **is** subject to the bundle and annual-prepay discounts, same as any
other monthly service. The spend is not. Discounting a pass-through would come
straight out of margin.

Paid media is four separate line items: Google Ads, Meta Ads, LinkedIn Ads and
TikTok Ads. Each carries its own monthly ad spend, but **the rate is set by
combined spend across every channel selected**, then applied to each channel's
own spend. Splitting $10,000 across four channels therefore costs the same to
manage as putting it all in one; charging each channel its own tier would have
penalised the client for diversifying.

The $1,000 minimum also applies once across paid media as a whole, not per
channel, so four channels do not stack four minimums. Where the minimum is what
is binding rather than the bands, the row says "minimum fee" instead of quoting
an overall rate that would read alarmingly high (the floor on $1,500 of spend
is 67%).

The fee is worked out once on combined spend and then apportioned back to the
channels by share. Rounding each channel independently let the line items miss
the real fee by a dollar or two, so each channel takes the difference between
the running total rounded at its own cumulative spend and at the previous one.
The lines sum to the fee exactly.

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

**Video Production is scoped by hours** rather than sold at a flat $4,000, at
**$150 an hour**. The quoted range is the hard rule: a $2,000 minimum project
fee and a $50,000 ceiling, with hours free to move between (13 to 334). At
$150 the rate does not land on those bounds exactly, so the price is clamped to
them at the extremes.

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

### The logo

The header draws the Duo Group mark (split ring, inner D, DUO wordmark) as
inline SVG, in `#logo-mark`. It is a **redraw**, not the official artwork file:
the logo was supplied as an image in conversation and never reached disk, so it
was rebuilt from what was visible. Two upsides fell out of that: it stays sharp
at any size, and the black half of the ring and the letterforms follow `--ink`,
so they invert in dark mode instead of disappearing. The wordmark is outlines
rather than `<text>`, so no font needs to load for it to render correctly.

**Check it against the real artwork before this goes to clients.** To swap in
the official file, open `service-builder.html`, find `var LOGO = "";` near the
top of the script, and paste a base64 data URI:

```
base64 -w0 <logo file>
```

Then `var LOGO = "data:image/png;base64,<paste>";`. Setting it hides the drawn
mark. Note a flat image will not invert in dark mode. The artwork has to be
inlined, the artifact sandbox blocks external image URLs. The source file is in
Drive under Client logos / Duo Group, or as `DUOGroupLogos.pdf`.

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
- The **paid media band ladder** is new. The band rates (50/40/35/32/30) came
  from the earlier whole-spend table; banding them keeps those rates while
  making the fee rise and the overall rate fall at every point.
- Against the old flat $1,500/account fee, this cuts revenue on small accounts
  (a $2,000 Meta-only client goes from $1,500 to $1,000) and on mid-size
  multi-channel ones (three channels was $4,500 flat; $10,000 of combined spend
  is $3,950). Worth checking against the delivery hours in
  `data/service-catalog.csv` before it goes to clients.
- The **$150/hr video rate** is a set rate, not derived from a past job. For
  reference the retired $4,000 flat price over its 40 recorded delivery hours
  worked out at $100/hr, so this is a 50% increase on that implied rate. The
  $2,000 floor and $50,000 ceiling are scoping decisions, not quoted jobs.

`data/service-catalog.csv` records every line with its source.

## Files

- `service-builder.html`: the menu
- `data/service-catalog.csv`: catalog with sources
- `data/paid-media-tiers.csv`: the ad-spend ladder
- `data/price-points-2026.csv`, `data/unit-costs-2026.csv`: reference data
- `archive/pricing-plan.html`: earlier pricing-rationale document, retired
