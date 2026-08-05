# A Best Self Storage — Design Brief

> Brief for the frontend agent implementing this site. Captures the goal, the vibe, the hard facts,
> and how to work with images. Deliberately does **not** prescribe colors, type, or layout — those
> are your call, guided by the vibe below. Last updated 2026-08-05.

## What this is

A single-page marketing site for **A Best Self Storage of Illinois LLC** — a family-run storage,
U-Haul, and rentable-space business in Downers Grove, IL. It replaces a dated site.

**The site has one job:** a nearby person who needs storage (or a truck, or cheap office/warehouse
space) lands here, trusts it within a few seconds, and calls. Judge every decision against that.

## The vibe

Warm, clean, and tasteful — first-class through **restraint**, not decoration. This is a real local
family business, and that human warmth is the whole edge over the big storage chains (Public Storage,
Extra Space), which all feel cold and interchangeable. Lean into: real, local, trustworthy, easy.

Guardrails:

- **No slop.** No stock photos of smiling strangers, no invented testimonials, no filler copy like
  "your journey starts here." Only true facts and the real photos.
- **Restraint is the sophistication.** Generous whitespace. One clear focal action (calling). Don't
  reach for gimmicks or concepts — a dim storage-hallway "hero," heavy motion, or novelty type would
  all be wrong. Basic, executed extremely well.
- Make the **phone call the obvious action.** That's the conversion.

Everything else — palette, typography, layout, motion — is yours to decide in service of that vibe.

## Positioning — the true selling points

1. **Family-run and local** — real people, in Downers Grove.
2. **One address for the whole move** — storage + U-Haul trucks + moving supplies + rentable
   office/warehouse space, in one place.
3. **Cheap and low-commitment** — $48/mo, first month free.

## Hard facts (real — use only these)

- **Name:** A Best Self Storage (of Illinois LLC)
- **Address:** 2333 Wisconsin Avenue, Downers Grove, IL 60515
- **Hours:** Monday–Friday, 8:00 AM – 5:00 PM
- **Pricing:** storage/lockers starting at **$48/month, first month free**
- **Services:** Lockers · Car storage · Office space · Warehousing · U-Haul truck rental · moving supplies
- **U-Haul:** authorized dealer on-site
- **Logo:** an existing small blue interlocking-knot mark (see image descriptions)

### Still needed from the owner (do NOT invent — leave a clear placeholder if unanswered)

- **Phone number** — not yet confirmed. This is the primary CTA, so flag it prominently as a
  placeholder until provided.
- **Email** — unknown; may not exist.

## Images — read this carefully

**Do NOT open or read any image file in `assets/source/`.** They are noisy and will pollute your
context. Work entirely from the descriptions below. When you want an image, you don't edit it
yourself — you **request** it (see protocol).

### What we have (source originals, in `assets/source/`)

- **`mom-uhaul.jpeg`** — the best asset, and the only one clean of watermarks. A high-resolution,
  authentic photo: the owner's mother, in sunglasses and a black-and-cream jacket, standing beside
  the front of a white U-Haul box truck in the facility's paved lot on a bright day. Behind her: the
  low brown-brick building, a green lawn with trees, a red hand-truck (dolly), and U-Haul moving
  blankets. Two signs are also in frame — the business's own sign, and a loud "$19.95 MOVING?" U-Haul
  promo banner. Warm, real, human. (The promo banners are visual clutter that can be cleaned.)
- **`interior-corridor-sparefoot-watermark.webp`** — a facility hallway: a receding row of
  galvanized-steel roll-up storage doors on both sides, each with a blue unit number, concrete floor,
  exposed ceiling with fluorescent lights. Carries a **SpareFoot watermark → do not publish as-is;**
  reference only.
- **`exterior-winter-yardi-watermark.jpg`** and **`exterior-autumn-sparefoot-watermark.jpg`** — the
  building seen from the street/lawn (one in winter, one in autumn), with the business's ground sign.
  Both **watermarked → do not publish.**
- **`front-sign-sparefoot-watermark.webp`** — a close-up of the real ground sign; source of the blue
  interlocking-knot logo mark and the address. **Watermarked → reference only.**

### Image protocol — you can shape images at will, via request

You may transform any image however the design needs — color grading, cleanup (e.g. removing the
promo banners), restyling, cropping, or generating a fresh matching detail — **as long as it never
fabricates a fake scene or a false claim.** You don't run the generator; the human does.

To request an image, write a short block the human can act on:

```
IMAGE REQUEST
  save as:  assets/<target-filename>
  from:     <source file, or "new">
  treatment: <plain-English description: grade to X, clean up Y, crop to Z, restyle as…, etc.>
```

The human runs it through an image generator and drops the result at that path. Reference the target
path in your code; if it isn't there yet, leave a clean placeholder so the layout holds.

## Domain & hosting (context — not your task)

Domain `abestselfstorageofillinois.com` is owned (GoDaddy, paid through 2026-12-27) but its
nameservers were pointed at a parking service, so it currently serves junk. Recovery is the owner's
GoDaddy task. The site will be hosted on **GitHub Pages** from this repo, so build it as a static,
self-contained page (no server, no tracking, no external build service required).
