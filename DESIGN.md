# A Best Self Storage — Design Doc

> Source of truth for the site rebuild. Nothing gets built that isn't decided here.
> Last updated 2026-08-05.

## What this is

A one-page marketing site for **A Best Self Storage of Illinois LLC**, a family-run storage +
U-Haul + rentable-space business in Downers Grove, IL. Replaces a dated hand-coded site whose
domain was hijacked by a parking service (see "Domain & hosting").

**The site has exactly one job:** a nearby person who needs storage (or a truck, or cheap
office/warehouse space) lands here, trusts it within a few seconds, and calls. Every element serves
that. Clean, warm, tasteful — good enough type and restraint to read first-class, without concept
gimmicks.

## Positioning — sell the truth, no filler

The edge over Public Storage / Extra Space is three honest things:

1. **Family-run and local** — real people, in Downers Grove.
2. **One address for the whole move** — storage + U-Haul trucks + moving supplies + rentable
   office/warehouse space, all in one place.
3. **Cheap and low-commitment** — $48/mo, first month free.

Rule: **no slop.** No stock photos of smiling strangers, no invented testimonials, no "your journey
starts here." Only true facts and the real photos.

## Verified facts (real — use only these)

- **Name:** A Best Self Storage (of Illinois LLC)
- **Address:** 2333 Wisconsin Avenue, Downers Grove, IL 60515
- **Hours:** Monday–Friday, 8:00 AM – 5:00 PM
- **Pricing:** storage/lockers starting at **$48/month, first month free**
- **Services (from the real sign):** Lockers · Cars · Offices · Warehousing · Fulfillment ·
  U-Haul truck rental · moving supplies
- **U-Haul:** authorized dealer on-site (real U-Haul location page, Downers Grove 60515)
- **Logo:** existing small blue interlocking-knot mark on the sign
- **Current web presence:** fixturedisplays.com/abest (a related family business)

### Needs owner confirmation (do NOT invent)

- [ ] **Phone number** — the sign reads `630-964-662_`; last digit(s) cut off in the photo. Confirm the full number.
- [ ] **Email** — none found anywhere. Is there one to list?
- [ ] **"& Fulfillment"** — the sign lists it. Still offered, or drop it?
- [ ] Unit sizes / a real price list beyond the $48 starting point — include a table, or keep it to "starting at $48"?

## Design direction

Warm and quiet, with a single confident point of color where people act. Restraint is the
sophistication.

### Color

```
Paper (bg)      #F6F4EF   warm off-white / bone — most of the page
Ink (text)      #1A1A17   near-black, faintly warm
Accent          #1E3A5F   deep confident blue, pulled from the real logo mark, warmed slightly
Line/subtle     #E4E0D8   hairlines, card edges, dividers
```

Accent appears on ~5% of the page: the call button, the phone number, links, a hairline or two.
Everything else is paper, ink, type, and one photo. No green (the sign's green is sun-faded, not a
brand color). No loud secondary colors.

### Type

- **Display / headlines:** one clean, confident sans (Archivo, semibold, lightly expanded feel).
- **Body:** a neutral, readable sans (IBM Plex Sans).
- **Numbers — prices, hours, phone, address:** mono (IBM Plex Mono), so they read like clear labels.
  This is the only "detail," and it stays quiet.

Self-hosted or Google Fonts; no other font dependencies.

### Layout (single page, generous whitespace)

```
┌───────────────────────────────────────────────┐
│  A Best Self Storage            630-964-662_ ▸  │  wordmark + call, sticky, quiet
├───────────────────────────────────────────────┤
│                                                │
│   Storage, space, and trucks                   │  plain confident headline
│   in Downers Grove.                            │
│                                                │
│   Family-run. $48/mo, first month free.        │  the real promise (mono price)
│   [ Call 630-964-662_ ]                        │  the one accent-colored action
│                                                │
│   [ mom + U-Haul photo, graded & cleaned ]     │  warm, real, human
├───────────────────────────────────────────────┤
│   WHAT WE OFFER                                │
│   ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐  │  plain clean cards, NO forced
│   │Lockers │ │ Cars   │ │Offices │ │Ware-   │  │  numbering (numbers only appear
│   │from $48│ │        │ │        │ │housing │  │  where they're actually real)
│   └────────┘ └────────┘ └────────┘ └────────┘  │
├───────────────────────────────────────────────┤
│   ONE ADDRESS FOR THE WHOLE MOVE               │  short line: truck + supplies +
│   U-Haul trucks · moving supplies · storage    │  storage, all here
├───────────────────────────────────────────────┤
│   [ map ]   2333 Wisconsin Avenue              │  location, hours (mono),
│             Mon–Fri 8–5   [ Call ▸ ]           │  big call button, family-run note
└───────────────────────────────────────────────┘
```

### Motion

Minimal: gentle fade/rise on scroll, a clear focus ring, subtle button hover. Respect
`prefers-reduced-motion`. Nothing that reads as AI-generated flourish.

### Quality floor

Responsive to mobile, visible keyboard focus, reduced-motion respected, real semantic HTML,
fast (static, self-contained, no tracking).

## Images

We can edit/restyle/regenerate the real photos to fit — **but never fabricate a fake scene or claim.**
Originals preserved in `assets/source/`. Edit recipes (to run through an image generator) are written
per-image once the direction is locked; the short version:

- **`mom-uhaul.jpeg` (hero):** color-grade to the warm paper/ink palette; clean out the loud `$19.95`
  promo banners in the background; keep it real. This is the anti-slop weapon — a real local family.
- **`interior-corridor` / `exterior` shots:** carry SpareFoot / Yardi **watermarks** — do not publish
  as-is. Use only as reference, or reshoot. Fresh real photos (a locker row, the office, a bay door),
  graded to match, are ideal later.
- **`front-sign`:** source of the logo mark and real service line; not for publishing (watermark).
- **Service cards:** clean, consistent treatment (real cropped details or simple marks), no stock.

## Domain & hosting

- **Domain is still owned** — `abestselfstorageofillinois.com`, GoDaddy, paid through 2026-12-27.
- **Problem:** nameservers were switched to **ParkLogic** (a parking service) on 2026-03-02, which is
  why it currently serves rotating redirect/ad pages. Fully recoverable.
- **Host:** GitHub Pages (this private repo), free and versioned.
- **Fix (owner does the GoDaddy steps):**
  1. Deploy the site to GitHub Pages.
  2. In GoDaddy: switch nameservers off ParkLogic back to GoDaddy defaults.
  3. Point DNS at GitHub Pages (A/AAAA + CNAME `www`), add the custom domain in repo settings.
  4. Confirm the GoDaddy login is secure — worth checking how the nameservers got changed.

## Open decisions for review

1. Confirm the phone number, email, "& Fulfillment," and whether to show a unit-size price table.
2. Approve the palette / type / layout above, or redirect.
