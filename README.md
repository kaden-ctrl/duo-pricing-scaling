# Duo Service Builder

A base package with add-ons underneath it, plus standalone services that can be
bought on their own. The bundle discount applies to the standalone services
only.

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
| LinkedIn | $500/mo |
| Google Business Profile | $500/mo |
| Reddit | $250/mo |

Each of the four social add-ons includes **$100 a month of boosting budget**.
That budget is inside the price, not billed on top, so the plan panel reports
it as "of which social boosting budget" rather than adding it to the total.

**Social add-ons are three static graphics a week.** If the client films a
video and wants it edited and posted, that is covered at the same price. That
covers Facebook, Instagram, LinkedIn and Google Business Profile.

**Reddit is different:** two relevant threads a week found and contributed to,
written in the client's voice. No graphics and no boosting budget, which is why
it is $250 rather than $500.

### Standalone services

These are their own services and do not need the base package.

| Service | Price |
|---|---:|
| Google Ads, Meta Ads, LinkedIn Ads, TikTok Ads | banded on combined ad spend, see below |
| Email Marketing | $500/mo |
| Video Production | $150/hr, $2,000 minimum, $50,000 cap |
| Website Build | $4,000 one-time |
| Website Management & Hosting | $100/mo |

The base package already carries a website and its upkeep, so Website Build and
Website Management & Hosting are there for clients who are not on the package.

### Paid media

Management is priced **in bands on combined ad spend**, like tax brackets. Each
band applies only to the part of the spend inside it, never the whole amount.

| Part of combined monthly spend | Rate on that part |
|---|---:|
| First $2,000 | 50% |
| $2,000 to $5,000 | 40% |
| $5,000 to $10,000 | 35% |
| $10,000 to $25,000 | 32% |
| Above $25,000 | 30% |

Minimum $1,000 a month, once across paid media rather than per channel. The fee
always rises with spend and the overall rate always falls. Ad spend itself is a
pass-through: it lands in the monthly total but is never discounted.

## How it works

| Standalone services selected | Discount |
|---:|---:|
| 1 | none |
| 2 | 5% |
| 3 | 8% |
| 4 | 12% |
| 5+ | 15% |

**The bundle discount does not apply to the base package or any of its
add-ons.** They are quoted as a package at list. Two consequences, both
deliberate:

- The discount comes off the **standalone services only**.
- Package add-ons **do not count toward the tier** either. Stacking add-ons
  cannot unlock a discount on the standalone services, which would otherwise be
  a way to buy the ladder cheaply.
- The ladder widget **stays out of the panel entirely** until a standalone
  service is in the plan, rather than sitting at 0% on a package-only quote.
  The prepay toggle shares that box and remains reachable either way.
- Where both are in play, the discount carries an asterisk: *add-on services
  within the base package are already discounted for being bundled with the
  base package, and do not contribute to the bundle discount*.

Annual prepay is **10% off everything**, package included, applied after the
bundle discount. It was not excluded, so it still runs across the whole plan.
Say the word if it should skip the package too.

One-time work (Website Build, Video Production) is never discounted.

- **Add-ons require the base package.** Selecting an add-on pulls the base in;
  turning the base off drops every add-on with it. Local monthly filming sits
  under Instagram the same way, so selecting it pulls in Instagram and, through
  Instagram, the base. Standalone services need none of this.
- **Minimum term is 12 months** whenever the base package, a website build or
  video production is in the plan.
- Selections persist per browser via `localStorage`. Saved state from an older
  version of the menu is reconciled on load, so an add-on whose parent is no
  longer selected is dropped rather than quoted on its own.

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
invoices. Every package and add-on price is now stated rather than assumed.
`data/service-catalog.csv` records each line as it now stands.
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
