# Duo Service Builder

An à la carte service menu. Pick services, and the bundle discount grows as
more are added.

**Deliverable:** [`service-builder.html`](service-builder.html)

## How it works

| Monthly services selected | Discount |
|---:|---:|
| 1 | — |
| 2 | 5% |
| 3 | 8% |
| 4 | 12% |
| 5+ | 15% |

Annual prepay (paid upfront) adds 10%. Combined discount is capped at 25%.

- The count uses **distinct monthly services**. Quantities inside one service
  (three social platforms, two locations) don't raise the tier. The whole AiR
  programme counts as one, and so does paid media across all three channels.
- **One-time build work is never discounted** — websites, video, landing pages
  and the visibility audit stay at list.
- **Paid media is priced as a share of ad spend** (see below), and that share
  is the management fee only. Ad spend itself is billed separately as a
  pass-through.
- Minimum term derives from the selection: 12 months where a build is included,
  6 months with Signal Sessions, otherwise month to month.

## Paid media management

The management fee is a percentage of monthly ad spend rather than a flat
per-account retainer. The more a client spends, the lower the rate.

| Monthly ad spend | Management |
|---|---:|
| Under $2,000 | 50% |
| $2,000 – $4,999 | 40% |
| $5,000 – $9,999 | 35% |
| $10,000 – $24,999 | 32% |
| $25,000 and up | 30% |

Minimum management fee is **$1,000 a month**, which is what carries the bottom
band: $1,000 of spend costs $1,000 to manage, and 50% doesn't start biting
until $2,000.

Two properties worth knowing before quoting it:

- The rate applies to the **whole spend**, not marginally. Crossing a tier
  lowers the fee outright — $4,999 of spend costs $2,000 to manage, $5,000
  costs $1,750. That's deliberate: it pays the client to move up.
- The fee **is** subject to the bundle and annual-prepay discounts, same as
  any other monthly service.

Meta, Google and LinkedIn are one line item now, priced off total spend across
all three. LinkedIn Job Posting and Retargeting & Dark Posts stay separate at
their flat monthly rates.

`data/paid-media-tiers.csv` holds the ladder with the fee at each band edge.

## Catalog

18 services across five categories — AI Search Visibility (AiR), Social Media,
Paid Media, Content & Creative, and Web & Search. Each carries a "What's
included" breakdown. Four presets (Local Presence, AI Visibility, Full Growth,
New Launch) pre-fill common combinations.

**AI Search Visibility is a single line** — the AiR Programme, $1,600 per
location per month, six-month minimum. It folds in what used to be four
separate items: the dashboard and tracking ($1,200/location), Signal Sessions
($400/mo), the baseline AI Visibility Audit (was $1,500 one-time) and
Multi-Location Reporting (was $350/mo). The audit and the roll-up are now
included rather than billed.

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

The artwork has to be inlined — the artifact sandbox blocks external image
URLs. The source file is in Drive under Client logos / Duo Group, or as
`DUOGroupLogos.pdf`.

## Where the prices came from

`duogroup.com` is blocked by this environment's network egress proxy, so the
catalog was assembled from what Duo actually contracts and invoices:

- Duo Pricing Sheet (June 2024)
- AiR client agreements — Kobico, CIS Office Furniture, Mill Forest Dental
- Santiam Hospital & Clinics services agreement
- Lawn Doctor 2026 options breakdown
- Monthly budget sheets, June–September 2026

Two prices are reconstructions rather than quoted figures and should be
confirmed: **Email Marketing** and the **Design Retainer**. The 2024 card lists
email at "$3,000/month," which reads as an all-in program price and conflicts
with the $200-per-extra-blast rate in the Santiam agreement.

Three more figures are constructions and are not traceable to a signed
agreement — they are pricing decisions, not sourced rates:

- The **$1,600 AiR Programme** price is the two monthly components added
  together ($1,200 + $400). Bundling the audit and the roll-up in gives away
  $1,500 of one-time revenue and $350/mo on multi-location accounts.
- The **paid media tier ladder** is new. It was built to two anchors — $1,000
  of spend costs $1,000 to manage, $5,000 of spend is managed at 35% — with
  the rate starting at 50% and bottoming out at 30%.
- Against the old flat fee, the tiers cut revenue on small single-channel
  accounts (a $2,000 Meta-only client goes from $1,500 to $1,000) and on
  multi-channel accounts (three channels was $4,500 flat; $15,000 of combined
  spend is now $4,800, and $6,000 is $2,100). Worth checking against the
  delivery hours in `data/service-catalog.csv` before it goes to clients.

`data/service-catalog.csv` records every line with its source.

## Files

- `service-builder.html` — the menu
- `data/service-catalog.csv` — catalog with sources
- `data/paid-media-tiers.csv` — the ad-spend ladder
- `data/price-points-2026.csv`, `data/unit-costs-2026.csv` — reference data
- `archive/pricing-plan.html` — earlier pricing-rationale document, retired
