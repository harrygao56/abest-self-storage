# Build Plan — A Best Self Storage

> Implementation plan derived from `DESIGN.md`. Written 2026-08-05.

## The one job

Local person needs storage, a truck, or cheap space → lands here → trusts it in ~4 seconds → calls.
Most will arrive on a phone. Every decision below is judged against that.

## Design thesis

**The chains sell a product. This sells a place and the people who run it.**

Public Storage, Extra Space, and CubeSmart all publish the same site: renders, stock smiles, a
rate-comparison table. The one thing they structurally cannot show is a real person standing in
front of a real building on a real street. So the hero is not a headline over a dim hallway — it's
the photo of the owner beside the truck, in the lot, on Wisconsin Avenue.

**Signature element: the caption.** Every real photo carries a short factual caption in the utility
face under a hairline rule, like an archive print — *"The owner, at our lot on Wisconsin Avenue."*
Nothing else on the page does this. It reads as documentary rather than marketing, costs nothing,
adds no gimmick, and is the single thing that makes the site unmistakably theirs. That's where the
boldness gets spent; everything else stays quiet.

## Tokens

### Color — concrete and steel, warmth from the photographs

Deliberately *not* a cream/terracotta page. The materials here are concrete floor, galvanized doors,
paved lot, brown brick, and one blue mark on the sign. The base is cool and clean; all the warmth
comes from the photos and one clay accent. Blue is also the real differentiator — orange is Public
Storage and U-Haul, green is Extra Space.

| Token | Hex | Role |
|---|---|---|
| `--concrete` | `#F1F2F0` | Page base — faintly cool grey-green, poured-floor neutral |
| `--ink` | `#16232B` | Body and display type; deep blue-black, steel in shadow |
| `--knot` | `#17548A` | The logo blue, off the real ground sign. Links, CTA |
| `--brick` | `#A5553A` | Muted building red. Accent, used maybe four times total |
| `--steel` | `#CBD2D4` | Hairlines, rules, dividers |
| `--white` | `#FFFFFF` | Card/panel surfaces that need to lift off concrete |

### Type — two families, three roles

Inverted from the usual serif-display/sans-body pairing.

- **Display — Archivo (variable, width ~115, weight 600–700).** A sturdy American grotesque that
  reads like painted signage and truck-door lettering. Confident, not fancy, correct for a
  Midwestern warehouse.
- **Body — Literata (variable).** A warm, screen-tuned serif at 18–19px. A serif body reads like a
  letter from a person, which is exactly the edge over the chains, and it's kind to older eyes.
- **Utility — Archivo condensed (width ~85), uppercase, tracked out.** Captions, labels, hours,
  address, tabular figures for the phone number and price. This is the "plate" voice.

Both self-hosted as woff2 in `assets/fonts/`. No CDN, no external requests.

### Motion

Near-zero, per the brief. One quiet page-load rise on the hero, and transitions on links/buttons.
No scroll-triggered reveals. `prefers-reduced-motion` kills all of it.

## Layout

```
DESKTOP                                    MOBILE
┌──────────────────────────────────────┐   ┌──────────────────┐
│ ◈ A BEST SELF STORAGE   (630)XXX-XXXX│   │ ◈ A BEST STORAGE │
├───────────────────────┬──────────────┤   ├──────────────────┤
│                       │              │   │ Storage in       │
│  Storage in Downers   │   [ photo:   │   │ Downers Grove,   │
│  Grove, run by the    │    owner +   │   │ run by the       │
│  family that owns it. │    U-Haul,   │   │ family that      │
│                       │    bleeding  │   │ owns it.         │
│  $48/mo · 1st mo free │    off top   │   │                  │
│                       │    & right ] │   │ $48/mo, 1st free │
│  ┌─────────────────┐  │              │   │                  │
│  │  CALL (630)…    │  │              │   │ [ photo ]        │
│  └─────────────────┘  │ ─────────────│   │ ─────────────────│
│  Mon–Fri 8–5          │ THE OWNER, AT│   │ THE OWNER, AT OUR│
│                       │ OUR LOT ON…  │   │ LOT ON WISCONSIN │
├───────────────────────┴──────────────┤   ├──────────────────┤
│  ONE ADDRESS FOR THE WHOLE MOVE      │   │ …sections stack… │
│  Lockers          Car storage        │   │                  │
│  Office space     Warehousing        │   ├──────────────────┤
│  U-Haul trucks    Moving supplies    │   │ ☎ CALL (630)XXX  │ ← sticky
├──────────────────────────────────────┤   └──────────────────┘   thumb bar
│  WHAT IT COSTS   $48 /mo, 1st free   │
├──────────────────────────────────────┤
│  U-HAUL, ON SITE  (+ optional photo) │
├──────────────────────────────────────┤
│  SPACE FOR YOUR BUSINESS             │
├──────────────────────────────────────┤
│  VISIT US   addr · hours · directions│
└──────────────────────────────────────┘
```

Sections, in order and why:

1. **Hero** — who, what, where, price, call. Split on desktop; text-first on mobile so trust lands
   before the image loads.
2. **One address for the whole move** — the six services as a plain two-column list on hairlines.
   No icons; icons are where this kind of page turns to slop.
3. **What it costs** — `$48` set large in the display face, `/month · first month free ·
   month-to-month`. One honest number, no table, no comparison chart.
4. **U-Haul, on site** — authorized dealer, trucks and supplies at the same address.
5. **Space for your business** — office and warehouse rental. A different audience than the
   household mover, so it gets its own short block rather than hiding in the service list.
6. **Visit us** — address, hours, and a "Get directions" link that opens the phone's own map app.
   No embedded map: an iframe is a third-party tracker and a slow, ugly rectangle.
7. **Footer** — name, address, hours, phone.

**The call is always one tap away:** phone in the desktop header, and a sticky bottom call bar on
mobile sitting in the thumb zone. Those two plus the hero button are the only primary buttons on the
page.

## Copy

Written plain and true. Sentence case, active voice, no filler. Working headline:

> **Storage in Downers Grove, run by the family that owns it.**
> Lockers from $48 a month, first month free. U-Haul trucks and moving supplies at the same address.

Nothing on the page will claim anything not in the brief's hard-facts list.

## Images to request

The page is built so it holds with clean placeholders if none of these arrive.

```
IMAGE REQUEST
  save as:  assets/hero-lot.jpg
  from:     assets/source/mom-uhaul.jpeg
  treatment: Remove the loud "$19.95 MOVING?" U-Haul promo banner and any other promo clutter,
             keeping the woman, the U-Haul truck, the brick building, the lawn and the business's
             own sign exactly as they are. Warm, natural grade — bright day, slightly lifted
             shadows, no heavy filter. Deliver two crops: a tall 4:5 for the desktop split hero and
             a 3:2 for mobile. Full resolution, then I'll size down.
```

```
IMAGE REQUEST
  save as:  assets/logo-knot.svg
  from:     assets/source/front-sign-sparefoot-watermark.webp
  treatment: Trace just the blue interlocking-knot mark from the ground sign into a clean flat
             single-color SVG on transparent background. No text, no sign, no watermark — the mark
             only. Also export assets/favicon.png at 512×512, mark on a white square.
```

```
IMAGE REQUEST  (optional — nice to have, page works without it)
  save as:  assets/corridor.jpg
  from:     assets/source/interior-corridor-sparefoot-watermark.webp
  treatment: Same corridor, same doors, same blue unit numbers — cleaned of the SpareFoot
             watermark, straightened, and lit a little warmer and brighter than the source. Must
             stay a true depiction of that hallway; don't restyle it into a different facility.
             16:9.
```

## Build

Static and self-contained for GitHub Pages: `index.html`, `styles.css`, `assets/`. No framework, no
build step, no JS beyond a few lines for the sticky bar if even that. Ships with:

- `LocalBusiness` JSON-LD (name, address, hours, price range) — real ranking value for
  "storage near me" searches, and free.
- Meta description, Open Graph tags, favicon.
- Responsive to 320px, visible keyboard focus, 44px tap targets, alt text on every image,
  `prefers-reduced-motion` honored.

## Open item — the phone number

The primary CTA has no number yet. It renders as **`(630) XXX-XXXX`** — 630 is genuinely Downers
Grove's area code, and the `XXX` reads as unmistakably unfinished so it can't be dialed by mistake
while holding the exact layout width. It lives in one place in the markup, flagged with an HTML
comment, and is a one-line find-and-replace when the owner confirms it. Same for email, if one
exists.
