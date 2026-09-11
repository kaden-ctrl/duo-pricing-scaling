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
  (three social platforms, two locations) don't raise the tier.
- **One-time build work is never discounted** — websites, video, landing pages
  and the visibility audit stay at list.
- **Paid media prices are the management fee only.** Ad spend is billed
  separately as a pass-through.
- Minimum term derives from the selection: 12 months where a build is included,
  6 months with Signal Sessions, otherwise month to month.

## Catalog

23 services across five categories — AI Search Visibility (AiR), Social Media,
Paid Media, Content & Creative, and Web & Search. Each carries a "What's
included" breakdown. Four presets (Local Presence, AI Visibility, Full Growth,
New Launch) pre-fill common combinations.

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

`data/service-catalog.csv` records every line with its source.

## Files

- `service-builder.html` — the menu
- `data/service-catalog.csv` — catalog with sources
- `data/price-points-2026.csv`, `data/unit-costs-2026.csv` — reference data
- `archive/pricing-plan.html` — earlier pricing-rationale document, retired
