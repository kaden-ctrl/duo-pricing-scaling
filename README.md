# Duo Service Builder

A base package with add-ons priced on top. Pick the add-ons, and the bundle
discount grows as more are added.

**Deliverable:** [`service-builder.html`](service-builder.html)

## The menu

### Base package

**AiR Dashboard, $1,500 a month.** Every plan starts here. Includes:

- Dashboard access
- New website
- Website updates and optimisation
- Weekly opportunities
- 2 blog posts a month
- Signal Sessions or weekly email

### Add-ons

Add-ons sit under the base package and cannot be quoted without it.

| Add-on | Price |
|---|---:|
| SEO | $250/mo |
| Facebook | $600/mo |
| Instagram | $600/mo |
| Local monthly filming (under Instagram) | +$200/mo |
| LinkedIn | $600/mo |
| Google Business Profile | $600/mo |

Each of the four social add-ons includes **$100 a month of boosting budget**.
That budget is inside the $600, not billed on top, so the plan panel reports it
as "of which boosting budget" rather than adding it to the total.

## How it works

| Monthly services selected | Discount |
|---:|---:|
| 1 | none |
| 2 | 5% |
| 3 | 8% |
| 4 | 12% |
| 5+ | 15% |

Annual prepay (paid upfront) adds 10%. Combined discount is capped at 25%. The
base package counts as one of the services.

- **Add-ons require the base package.** Selecting an add-on pulls the base in;
  turning the base off drops every add-on with it. Local monthly filming sits
  under Instagram the same way, so selecting it pulls in Instagram and, through
  Instagram, the base.
- **Minimum term is 12 months**, because the base package includes a new
  website build.
- Selections persist per browser via `localStorage`. Saved state from an older
  version of the menu is reconciled on load, so an add-on whose parent is no
  longer selected is dropped rather than quoted on its own.

## Open questions

Two things were assumed when this was built and should be confirmed:

- **Instagram, LinkedIn and Google Business Profile are priced at $600**, the
  same as Facebook. Only Facebook carried a stated price; the others were
  listed with their boosting budget but no number.
- **The bundle discount and annual prepay were kept** from the previous
  version. Neither was mentioned in the current spec. With everything selected
  the plan reaches the 15% tier, which takes $4,350 of list down to $3,698.

## What this replaced

The previous build was a flat a la carte menu of 11 services with a banded
paid media calculator. Retired in this rebuild:

- **Paid media** as separate Google, Meta, LinkedIn and TikTok Ads line items,
  along with the whole banded management-fee engine (50/40/35/32/30 on combined
  ad spend, $1,000 minimum) and the ad-spend pass-through in the total. Social
  boosting budget replaces it at a much smaller scale.
- **Video Production** priced by production hours at $150/hr.
- **Email Marketing**, **Website Build** and **Website Management & Hosting**
  as standalone lines. The website is now inside the base package.

All of it is in git history if any piece needs to come back.

## Branding

From the Brand Guidelines doc (Duo Group entry):

- Blue `#019ED0`, white `#FEFEFE`, black `#000000`
- Typeface **Avenir Next LT Pro**, with Mulish substituting where it isn't installed
- AiR purple `#9A76D6` marks the base package

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

The current menu is a pricing decision, not a reconstruction from past
invoices. `data/service-catalog.csv` records each line as it now stands.
`data/price-points-2026.csv` and `data/unit-costs-2026.csv` keep the older
reference data from when the catalog was assembled out of signed agreements
(Duo Pricing Sheet June 2024, AiR client agreements, the Santiam Hospital and
Lawn Doctor breakdowns, and the June to September 2026 budget sheets).

## Files

- `service-builder.html`: the menu
- `dist/index.html`: the published copy, identical to the above
- `data/service-catalog.csv`: the menu as data
- `data/price-points-2026.csv`, `data/unit-costs-2026.csv`: older reference data
- `archive/pricing-plan.html`: earlier pricing-rationale document, retired
