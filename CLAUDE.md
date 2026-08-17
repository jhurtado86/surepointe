# CLAUDE.md — Surepointe Lab

## What This Is — FILL PER CLIENT (boilerplate frozen)

This is the **Surepointe Lab** website, built on the Nexor AI template.
The generic template placeholders are resolved to this client's real identity below;
anything not yet confirmed is left `[NEEDS INPUT]` and must NOT be invented. Keep the
template's structure, section rhythm, nav pattern, dark sections, footer layout, and
design system intact — only content, brand, service area, colors, logo, photos, and copy
are client-specific.

Trade: **Medical diagnostic laboratory — accepts most insurances + self-pay; no doctor's
order required; walk-ins welcome.** Several template modules are home-services artifacts
that do not apply to this trade — see "Template Sections to DELETE."

Treat any remaining `[NEEDS INPUT]` field as fill-in-the-blank. Do not invent client
facts; confirm with the client / Juan before filling.

---

## Resolved token reference — FILL PER CLIENT

| Token | Resolved value |
|---|---|
| Business name | Surepointe Lab (short brand: Surepointe Lab) |
| Service One | Blood Work & Lab Testing |
| Service Two | Drug Testing |
| Service Three | Paternity Testing |
| Service Four | Wellness Panels |
| Service Five | Hormone Testing |
| Service Six | Gender Reveal Testing |
| service slugs | blood-work-lab-testing / drug-testing / paternity-testing / wellness-panels / hormone-testing / gender-reveal-testing |
| Primary city | Pharr (physical location; anchors NAP + homepage) |
| City 2 | McAllen |
| City 3 | Edinburg |
| City 4 | Mission |
| City 5 | Weslaco |
| City 6 | San Juan |
| City 7 | Alamo |
| City 8 | Donna |
| city slugs | mcallen / edinburg / mission / weslaco / san-juan / alamo / donna *(no pharr slug — homepage serves Pharr)* |
| Region | Rio Grande Valley (RGV) / Hidalgo County, TX |
| Phone (site) | (956) 586-6463 — GHL tracking number, delivered and live site-wide |
| Email | Surepointelab@jigmed.org |
| Domain | www.surepointelab.com — canonical host confirmed as www; set as Vercel Primary day one |

> ⚠️ **Email domain differs from website domain.** Email is @jigmed.org; website is
> surepointelab.com. Both confirmed correct — do NOT "fix" one to match the other,
> and never build a URL off the email domain.

> ⚠️ **8 cities served, 7 city pages.** Flexed above the default 6 and justified by the
> RGV corridor footprint — all 8 lie within ~30 miles along US-83 / Business 83. Pharr
> has no city page of its own: the homepage serves that intent (see Site Architecture).

---

## Brand color system — FROZEN methodology, FILL the values

Palette is **derived from the client logo every build** — extract the hexes from
`brand_assets/logo.png`; never assume the template's colors. Define once via CSS custom
properties + Tailwind `theme.extend.colors`; reuse everywhere; never hardcode hexes per
page.

| Token | Hex | Role |
|---|---|---|
| `--color-primary` | `#C0121A` | Deep crimson red — hero/sections, footer, nav, primary buttons |
| `--color-primary-mid` | `#9E0F16` | Darker crimson — hover states, secondary buttons, borders on dark |
| `--color-accent` | `#1852D4` | Royal blue — use on LIGHT/WHITE backgrounds only (EKG/swoosh origin) |
| `--color-accent-bright` | `#CFE0FF` | Light blue — use on DARK (red) backgrounds only; icons, eyebrow, highlights |
| `--color-accent-deep` | `#1240A8` | Deeper blue — on-light fallback for small text, dividers on white |
| `--color-dark` (canonical) | `#C0121A` | [= primary] THE single dark-section background token |
| `--color-dark-3` | `#8A0D12` | Deepest crimson — pressed states, deepest card backgrounds on dark sections |
| `--color-silver` / neutral | `#E2E3E8` | Cool light gray — muted borders, secondary text on dark, chrome |
| `--color-bg` | `#FFFFFF` | Primary body/content background |
| `--color-bg-2` | `#F5F5F7` | Secondary background — alternating section tint, card backgrounds on light |
| `--color-ink` | `#111214` | Near-black — primary headings/body text on light backgrounds |
| `--color-muted` | `#6B6E7A` | Blue-gray muted secondary text |
| `--color-muted-light` | `#A0A3AD` | Lighter muted — captions, helper text, placeholders |
| `--color-line` | `#E2E3E8` | Borders and dividers (= silver; aliased for clarity in brand.css) |
| `--color-rating` | `#F5A623` | Star rating gold — review widget stars only |
| `--nav-height` | `136px` | Navbar height — consistent across all pages; clears the 112px logo with 24px breathing room |
| `--nav-logo-height` | `112px` | Logo height inside the navbar — matches the footer |
| `--footer-logo-height` | `112px` | Logo height inside the footer |

**FROZEN rules:**
- **Accent split by background — CRITICAL:** `#1852D4` on `#C0121A` = 1.04:1 contrast
  (invisible). The two accent tokens have strictly split roles and must NEVER be swapped:
  — `--color-accent` (`#1852D4`) → LIGHT/WHITE backgrounds only
  — `--color-accent-bright` (`#CFE0FF`) → DARK (red) backgrounds only; icons, eyebrow,
    highlights; measured 4.71:1 on `#C0121A`, clears AA for small text
- **Accent-deep on-light fallback:** `--color-accent-deep` (`#1240A8`) is the fallback for
  small accent text or thin dividers on white where `#1852D4` goes low-contrast.
- **One canonical dark token:** `--color-dark` (`#C0121A`) is the only dark-section
  background. Never let a second near-identical dark hex drift in.
- **Red is the confirmed brand primary.** The Surepointe Lab logo is built entirely around
  deep crimson red (`#C0121A`) — the outer ring, the blood drop icon, the whole identity.
  This is NOT the template's decorative red; it IS the brand. Red stays as
  `--color-primary` and `--color-dark`. Never drift to a different red shade.
- **Never use default Tailwind blue/indigo/sky/cyan.** The only blues allowed are
  `#1852D4` (on light) and `#CFE0FF` (on dark). No other blue enters the design.

---

## Integration placeholders — FROZEN insertion points, DECIDE per client

- `<!-- GHL CONTACT FORM EMBED -->` — [NEEDS INPUT — GHL confirmed; embed code coming from client].
- `<!-- GHL CHAT WIDGET SCRIPT -->` — [NEEDS INPUT — GHL confirmed; script coming from client] (insert before `</body>`).
- `<!-- GHL EXTERNAL TRACKING SCRIPT -->` — [NEEDS INPUT — GHL confirmed; script coming from client] (insert in `<head>`).
- `<!-- GHL REVIEW WIDGET EMBED -->` — INCLUDE. GHL review widget confirmed. Wire on build;
  embed code coming from client. Once wired, `aggregateRating` (4.9 / 232 reviews) is
  cleared for JSON-LD on the homepage.
- `<!-- GOOGLE MAPS EMBED -->` — INCLUDE. Confirmed public address at Pharr Medical Complex.
- `<!-- INSURANCE CARRIER LOGO ROW -->` — DELETE. "Accepts most insurances" — no specific
  carrier partnerships confirmed. Copy only, never a logo wall.
- `<!-- FINANCING SECTION -->` — DELETE. Not applicable to a diagnostic laboratory.
- Social share image: `brand_assets/og-image.jpg` (1200×630) — [NEEDS INPUT — create before launch].

---

## Template Sections to DELETE for this client — FROZEN candidates, FILL the list

- Financing block / CTA — DELETE (not applicable)
- Insurance carrier-logo row — DELETE (no specific carriers confirmed; copy only)
- Review widget / star rating / review-count blocks — INCLUDE via GHL review widget
  (embed code coming; wire on build)
- Inventory / gallery page — DELETE (medical lab; no product inventory)
- Trust-badge pill row in the hero — delete by default (redundant with the eyebrow)
- Any home-services-specific artifact (roofing, HVAC, contracting, "free estimate,"
  home-services framing) — DELETE and rewrite entirely for medical lab context

---

## Business Identity — FILL PER CLIENT (guardrails frozen)

Every field is confirmed from onboarding or flagged `[NEEDS INPUT]`. Nothing inferred.

- **Business name / short brand:** Surepointe Lab
- **Industry / trade:** Medical diagnostic laboratory — accepts most insurances + self-pay;
  no doctor's order required; walk-ins welcome; in-shop + Home Draws
- **Owner:** Not published on this site. **FROZEN rule:** owner name is referenced only
  in a dedicated "About the Owner" section or where genuinely required — never threaded
  through general body copy, headings, meta/OG, or CTAs. Client has confirmed: do not
  publish owner name. About page focuses on the business story and mission only.
- **Staff / team:** [NEEDS INPUT — names + roles not published on current site].
  **Never infer staff or roles from social posts. Confirm directly with the client.**
- **Relationship claims:** **FROZEN** — no "family owned," "husband and wife," "couple," or
  any relationship structure without explicit written confirmation. "Family-run" is a
  tone signal (safe); a relationship *claim* is a fact (needs confirmation). [NEEDS INPUT]
- **Differentiator / ownership signal** (e.g. veteran-owned): [NEEDS INPUT — confirmed only]
- **Owner background (for About page):** Not published. About page tells the business
  story — founding, mission, values — without referencing the owner by name or background.
- **FROZEN framing rule:** an experience figure is a PERSONAL claim, not a business-age
  claim. Current site states "over 25 years of experience" — write "over 25 years in
  laboratory diagnostics" — never "over 25 years serving [City]" (implies business age).
  [NEEDS INPUT — confirm "25 years" refers to personal/team experience before publishing]
- **Supplier / franchise / dealer relationship:** SneakPeek® is a third-party branded
  product used for Gender Reveal testing. See Locked Language for copy rules.
- **Physical address:** 1002 W Sam Houston Blvd, Suite 9, Pharr, TX 78577 — inside
  Pharr Medical Complex. Public address confirmed → PostalAddress INCLUDED in schema.
- **Phone (site):** (956) 586-6463 — GHL tracking number, delivered and wired site-wide.
  NOTE: the hero video and the home2 storefront photo both show 956-586-0993, a
  DIFFERENT number. Neither is the tracking number; confirm with the client whether
  956-586-0993 is still in service before launch.
- **Phone (owner personal — NOT FOR PUBLICATION):** [NEEDS INPUT — record here only so
  it is never mistaken for the site number; must return zero grep hits before deploy]
- **Email:** Surepointelab@jigmed.org [domain is jigmed.org, NOT surepointelab.com —
  do not "fix"; do not build any URL off the email domain]
- **Domain + canonical host:** www.surepointelab.com — confirmed; set as Vercel Primary day one
- **Founded:** May 2013 — confirmed by client; cleared to publish in copy and schema
- **Licenses / certifications:** None confirmed. Publish no certification claims.
- **Official tagline:** [NEEDS INPUT — no official tagline identified]
- **Review / reputation status:** 4.9 stars / 232 Google reviews (as of 2026-08-17).
  GHL review widget confirmed for display and wired. `aggregateRating` cleared for JSON-LD.
  ⚠️ **reviewCount is a moving number — re-sync periodically.** It has drifted 226 → 227
  → 232 across three checks. The live GHL widget is the source of truth, not this file:
  read the count off the widget, then update BOTH the homepage `aggregateRating` and
  this file in the same pass. Schema that disagrees with the on-page widget is a rich-
  results problem. Re-check any time the homepage schema is touched.
- **Price range:** [NEEDS INPUT — for JSON-LD `priceRange` only; never in copy]

### Key operational facts — confirmed
- **Service model:** In-shop walk-in (1002 W Sam Houston Blvd, Ste 9, Pharr, TX 78577) +
  Home Draws (no service area or travel radius published)
- **No doctor's order required** — confirmed; safe to publish
- **Walk-ins welcome** — confirmed; safe to publish
- **Insurance:** Accepts most insurances + self-pay. Never name specific carriers. Never
  promise coverage outcomes. Route coverage questions to "call us to confirm your coverage."
- **Intake method / primary CTA framing:** Walk in or call (956) 586-6463
- **Confirmed differentiators:** No doctor's order required · No referral needed · Accepts
  most insurances · Self-pay option · Walk-in friendly · Located in Pharr Medical Complex ·
  Home Draws available · Founded 2013

### Hours — CONFIRMED (GMB is authoritative)

| Day | Hours |
|---|---|
| Monday – Friday | 7 AM – 5 PM |
| Saturday | 8 AM – 11:30 AM |
| Sunday | Closed |

Use these hours for `openingHoursSpecification` in JSON-LD and all on-page display.
GMB hours are the confirmed source of truth. The after-hours appointment window
(5:30PM–7PM) mentioned on the old site is NOT carried forward — not confirmed still active.

---

## Services — FROZEN methodology, FILL the six

**FROZEN:** select service pages for search volume + lead intent (broad high-intent
categories over narrow component terms). Minor/related services fold in as on-page
sections or FAQ, not their own pages.

- **Flagship (highest volume + call volume):** Blood Work & Lab Testing
- **Secondary push (differentiator / highest ticket):** Drug Testing
- **Standard ×4:** Paternity Testing · Wellness Panels · Hormone Testing · Gender Reveal Testing

**Folded-in sub-services (sections/FAQ, NOT their own pages):**

*Blood Work & Lab Testing page:*
— Individual tests: CMP, CBC, Lipid Panel, Urinalysis, PSA, Hemoglobin A1C, Sed Rate,
  Ca125, PT (Prothrombin Time), Microalbumin, HCG Serum, Free T4
— Infectious disease: COVID-19 (Rapid & PCR), Strep A, Flu A&B, RSV,
  H-Pylori (Breath & Blood), HIV, Pregnancy Testing (Blood & Urine)
— Home Draws: mention here and on Wellness Panels + Hormone Testing pages;
  no service area published; no dedicated page

*Drug Testing page:*
— Urine Drug Screen · Hair Follicle Drug Test · DOT Drug Testing (all three as sections)

*Wellness Panels page:*
— Branded packages: SurePower Check (Men Wellness) · Surepointe Check (Basic Wellness) ·
  Wonder Woman Check (Women Wellness) · Surepointe Plus · Super Surepointe · Arthritis Profile
— General Wellness Panels umbrella

*Hormone Testing page:*
— Free & Total Testosterone · Estrogen Panel · Thyroid Panel (T3 Uptake, T4, TSH,
  Thyrox, Free T4)

*Gender Reveal Testing page:*
— SneakPeek® Early Gender Test — fetal sex detection as early as 6–7 weeks gestation.
  See Locked Language for copy rules (no accuracy percentage).

> ⚠️ **FROZEN anti-cannibalization:** keep distinct search intents on distinct pages.
> Drug Testing and Blood Work are separate buyer intents — keep them separate.
> Hormone Testing and Wellness Panels both involve blood draws but serve distinct search
> intents (targeted health concern vs. general health screening) — keep them separate.

> ✅ **"Wonder Woman Check"** — confirmed correct spelling throughout. The current site's
> "Wonder Women" was a typo. Use "Wonder Woman Check" everywhere.

> ✅ **"A1C"** — confirmed correct abbreviation throughout. The current site's "AIC" was
> a typo. Use "A1C" everywhere (Hemoglobin A1C, A1C panel, etc.).

---

## Site Architecture — FROZEN structure, FILL the slugs

> ⚠️ **FROZEN — VERIFY BEFORE WRITING PATHS.** After cloning the template and before
> finalizing any path here, run `find . -name "*.html"` and confirm the real tree matches.
> Prior builds shipped `CLAUDE.md` paths that didn't match the repo and paid for it every
> session. **Disk is the source of truth.**

- Homepage `index.html`
- About `about.html`
- Contact / Thank-You `thank-you.html` (noindex, nofollow)
- 6 service pages under `/services/`:
  - `blood-work-lab-testing.html`
  - `drug-testing.html`
  - `paternity-testing.html`
  - `wellness-panels.html`
  - `hormone-testing.html`
  - `gender-reveal-testing.html`
- 7 city pages under `/areas/`: *(8 cities served; Pharr has no page of its own — see below)*
  - `mcallen.html`
  - `edinburg.html`
  - `mission.html`
  - `weslaco.html`
  - `san-juan.html`
  - `alamo.html`
  - `donna.html`
- **No `pharr.html`.** The homepage IS the Pharr page — it carries the NAP, the address,
  the hours and the `DiagnosticLab` entity, and a separate city page would cannibalise it.
  Pharr stays in the Areas We Serve dropdown and the footer, pointing at `/`; the
  homepage service-area card points at `/#contact`. Pharr remains in `areaServed` in
  schema and in body copy — it is a served city, just not a separate URL.
- No inventory / gallery page

### City priority — FROZEN methodology, FILL the order
Pharr anchors the homepage + NAP. McAllen is the highest-volume keyword target and
becomes the CITY-PAGE TEMPLATE. Order drives GSC indexing sequence.

1. **Pharr** — physical location; anchors NAP, homepage, all schema. Home base.
   NO separate city page — the homepage IS the Pharr page.
2. **McAllen** — largest RGV city; highest search volume; primary keyword prize;
   CITY-PAGE TEMPLATE — all remaining city pages inherit this one.
3. **Edinburg** — Hidalgo County seat; strong population; likely second-highest volume
4. **Mission** — solid market; US-83 / Business 83 corridor
5. **Weslaco** — east valley anchor; covers Donna/Weslaco corridor
6. **San Juan** — close proximity to Pharr; strong Home Draws candidate
7. **Alamo** — fills gap between San Juan and Weslaco
8. **Donna** — easternmost city; completes the US-83 corridor coverage

---

## Always Do First — FROZEN
Invoke the frontend-design skill before writing frontend code **if available** in the
environment (it may not be installed in Claude Code — proceed without it if not).

## Content Writing Methodology — FROZEN
For all page copy, read and follow `SEO-CONTENT-PROMPT.md` in full as the PRIMARY writing
methodology before writing any content. If wording ever conflicts with the technical rules
below, `SEO-CONTENT-PROMPT.md` wins on wording; the rules below govern technical
implementation.

---

## Local SEO Requirements — FROZEN (fill only the title/description tokens)

**Per-page metadata (every page):** unique `<title>` <60 chars; unique
`<meta description>` <160 with a service + city + CTA; local `keywords`;
`robots` index/follow with max-image/snippet/video-preview; self-referential `canonical`;
`<html lang="en">` + viewport.

**Open Graph + Twitter (every page):** og:title/description/url/type/image/locale/site_name;
twitter summary_large_image + title/description/image; images → 1200×630 (flag if not created).

**Structured Data (JSON-LD) — FROZEN patterns:**
- **Homepage:** `@type: "DiagnosticLab"` (most accurate Schema.org subtype for a
  patient-facing diagnostic laboratory; do NOT use bare LocalBusiness). Include name,
  telephone (GHL number — pending), email, priceRange (pending), `openingHoursSpecification`
  (GMB hours confirmed above), `areaServed` (all 8 cities), `hasOfferCatalog` (all 6
  service pages).
- **PostalAddress:** INCLUDE — confirmed public address (1002 W Sam Houston Blvd, Ste 9,
  Pharr, TX 78577).
- **`aggregateRating`:** INCLUDE once GHL review widget is wired. Values: ratingValue 4.9,
  reviewCount 232 (as of 2026-08-17), bestRating 5. Wire together with the widget — never
  one without the other. reviewCount drifts upward as reviews accumulate — re-read it off
  the live widget and re-sync it here and in Business Identity whenever this block is touched.
- License numbers → `additionalProperty` — none confirmed; omit until confirmed.
- **Service pages:** 3 blocks — `Service` + `FAQPage` (min 6 Q&As) + `BreadcrumbList`.
- **City pages:** 3 blocks — `DiagnosticLab` ref (same `@id` as homepage, NOT a
  re-declaration) + `FAQPage` (min 4 city-scoped Q&As) + `BreadcrumbList`.
  `areaServed` = that city only, never the full list.
- **Thank-you trio (one atomic unit):** noindex/nofollow meta + excluded from `sitemap.xml`
  + Disallow in `robots.txt`.
- **Per-page title collision:** the flagship service title must lead with a different
  phrase than the homepage title even when they share a keyword.
- **Offer-catalog count == live service-page count (6).**
- Validate at `search.google.com/test/rich-results` before launch.

**Visible on-page SEO — FROZEN:** exactly one `<h1>`/page; H2/H3 hierarchy, no skipped
levels; city names in human-readable body text; service+city combos appear naturally;
descriptive alt text with service/location context.

**City pages — anti-duplicate — FROZEN:** each city page ≥30–40% unique content; never
just swap the city name (doorway-page penalty); reference real, VERIFIED local anchors
(highways/neighborhoods/landmarks/districts) — flag `[VERIFY]` rather than invent; unique
intro + unique "why [City] chooses us" per page.

**Technical SEO files — FROZEN:** `sitemap.xml` (all indexable pages; exclude thank-you);
`robots.txt` (allow crawl, disallow thank-you, point to sitemap).

**Title/description patterns — FILL:**
- Homepage: `Pharr Lab Testing | Self-Pay & Insurance | Surepointe Lab` (57 chars)
- Service page: `[Service Name] in Pharr, TX | Surepointe Lab`
- City page: `Affordable Lab Testing in [City], TX | Surepointe Lab`

---

## Hero & Asset Patterns — FROZEN

### Hero + Final-CTA backgrounds — dedicated named slots ONLY
- The hero background and the final-CTA background are **their own asset slots.** They are
  filled **only** by a purpose-made image named exactly `hero-background.*` and
  `cta-background.*` in `brand_assets/`.
- **They NEVER use a client content/job photo.** A client's section/gallery photos are
  never promoted into either background. Ever.
- Until the dedicated file exists, both stay on `https://placehold.co/1920x1080` at exact
  final dimensions. Flag as pending — never substitute another image to "fill" it.
- **Off-limits on every content-photo and layout pass.**
- Static full-bleed image is the default hero on every page including the homepage
  (`min-h-screen`, left-anchored text block, image + dark overlay ~0.7 + edge vignette +
  text-shadows).

### Hero video — enhancement, homepage only
**Confirmed: client will provide a hero video clip.** Client has a YouTube video at
https://youtu.be/h7GuJlfmFrs (currently on About page) — raw clip is coming.
Replaces the static homepage hero; `hero-background` image becomes the poster/fallback.
**FROZEN sequence, never skipped:** trim only → save preview → client approves in/out →
compress separately (H.264, strip audio, ~2–3MB) → wire in last. `.gitignore` the raw
source + trim preview; commit only the final compressed clip. Build homepage with static
hero first; swap to video when clip is delivered.

### Uniform photo sizing — every section, every page
- **Every content photo uses the same-size aspect-ratio container** (`aspect-ratio` +
  `object-fit: cover`), never a fixed `h-[Npx]`. One ratio applied site-wide so no photo
  is a different size than another within or across sections.
- This is independent of the photo *tier* (which sets how MANY photos a page gets, below).
  Tiers govern count; this rule governs that every container is the same dimensions.

### Gallery / inventory section — uniform grid, no dead space
Not applicable — no inventory or gallery page for this client.

### Photo Tier Allocation — FROZEN default (override per client at strategy lock)
| Page type | Body photos | Hero |
|---|---|---|
| Flagship service (Blood Work & Lab Testing) | 5 | ✓ |
| Secondary push service (Drug Testing) | 3 | ✓ |
| Standard service ×4 | 2 each | ✓ |
| City page ×8 | 1 each | ✓ |
| About | 2 (no owner portrait — owner not published) | ✓ |

**FROZEN rules:** one-photo-one-slot on all non-inventory pages (no photo twice on a
page); cross-page reuse minimized; excluded types everywhere — readable license plates,
strong tilt/rotation, stained/damaged subjects, anything privacy-sensitive; owner/people
slots use `aspect-[3/4]` + `object-position: center top` (portrait is the norm for
headshots); document EXACT asset filenames confirmed by `ls brand_assets/` — never assume
naming.

### City-page clone zones — FROZEN
Four unique zones per city, everything else shared:
`<!-- CITY-SWAP: intro -->` · `<!-- CITY-SWAP: local-anchors -->` ·
`<!-- CITY-SWAP: why-city -->` · `<!-- CITY-SWAP: faq -->`
The Areas We Serve dropdown (desktop + mobile) is a protected shared zone — mark it and
never modify it during a city clone pass:
`<!-- SHARED ZONE: Areas We Serve dropdown — do NOT modify during city clone pass -->`

---

## Screenshot discipline — FROZEN (tiered)

Code MUST save real PNG files to `./temporary screenshots/` and report the exact path — a
prose description is never a substitute. **Number of rounds is tiered by page type:**

- **Gated template pages — homepage, flagship service (Blood Work & Lab Testing), deepest
  city (McAllen): 2 comparison rounds.** These set the pattern everything inherits;
  iterate until right.
- **Clones and structural pages — remaining services/cities, about, thank-you: 1 round +
  a click-through.** They inherit an approved parent, so verify, don't re-iterate.
- More rounds only if the 1-round check surfaces a real problem.

(Serve on localhost first — never screenshot a `file:///` path.)

---

## Reference Images — FROZEN
Default: build ORIGINAL pages from this file with high craft — do NOT match a provided
reference. The match-exactly rules apply ONLY when a reference image is explicitly
provided (then: match layout/spacing/type/color, swap placeholder content, don't improve
the design, 2 comparison rounds).

## Local Server / Screenshot Workflow — FROZEN
`node serve.mjs` (root at `http://localhost:3000`, background, don't double-start).
`node screenshot.mjs http://localhost:3000 [label]` → `./temporary screenshots/screenshot-N[-label].png`
(auto-incremented). Read the PNG back and analyze specifics (px sizes, exact hexes,
spacing, alignment, radii, shadows).

## Output Defaults — FROZEN
Self-contained HTML; Tailwind via CDN; `https://placehold.co/WIDTHxHEIGHT` placeholders;
mobile-first responsive.

## Anti-Generic Guardrails — FROZEN
Brand tokens only (never default Tailwind palette). Layered color-tinted shadows (never
flat `shadow-md`). Distinct display + body fonts; tight tracking on large headings,
generous body line-height. Layered radial gradients + SVG-noise grain for depth. Animate
only `transform`/`opacity` (never `transition-all`), spring easing. Every clickable
element has hover + focus-visible + active states. Image overlays + a color-treatment
layer. Intentional spacing tokens. A base→elevated→floating depth system.

---

## Locked Language — FROZEN framework, FILL per client
Freeze anything that must never drift:
- **Insurance framing:** "accepts most insurances" — never name a specific carrier; never
  promise coverage outcomes or $0 amounts; route coverage questions to "call us to confirm
  your coverage"
- **Warranty:** [NEEDS INPUT — publish no warranty or guarantee scope until confirmed in writing]
- **Certification/quality claims:** None confirmed. Publish no certification claims (no
  CLIA, CAP, AABB, or other cert language) until confirmed in writing.
- **Ownership signal:** [NEEDS INPUT — confirmed only; do not infer from social]
- **Experience framing:** "over 25 years in laboratory diagnostics" — personal/team
  experience, NOT business age. Never write "over 25 years serving [City]."
  [NEEDS INPUT — confirm exact wording and that this is a personal/team claim]
- **Founded year:** May 2013 — confirmed; cleared to use in copy and schema
- **Owner name:** Not published on this site. About page tells business story only.
- **Testimonials/reviews:** GHL review widget confirmed for display. No manually written
  or unattributed testimonials. 4.9 / 232 cleared for `aggregateRating` (count re-syncs
  against the live widget — see Review / reputation status).
- **SneakPeek® claims:** Reference the test by name and describe what it detects (fetal
  sex, as early as 6–7 weeks into pregnancy). Do NOT state any specific accuracy
  percentage (not "99.9%" or any other figure) — best approach is to let the service
  description speak without a numerical claim.
- **Pricing:** no price / range / "starting at" in copy, FAQ, or JSON-LD Offer blocks —
  route all pricing intent to "call for pricing"
- **No doctor's order / walk-ins:** "no doctor's order required" and "walk-ins welcome"
  are confirmed and cleared to publish everywhere
- **Social media:** Footer includes Facebook and Instagram only.
  Facebook: https://www.facebook.com/profile.php?id=100093646171998
  Instagram: https://www.instagram.com/surepointe_lab/
  Twitter/X: dropped — do not include anywhere on the site.

## Hard Rules — FROZEN
- No invented facts; confirm before filling any `[NEEDS INPUT]`.
- No price / range / "starting at" unless explicitly confirmed here — route pricing intent
  to the call CTA (applies to copy, FAQ, AND JSON-LD Offer blocks).
- No insurance coverage-outcome claims.
- No relationship claim without written confirmation.
- Never infer ownership/roles/relationships from social posts.
- Never publish the owner's personal number — GHL tracking number only; grep returns zero
  hits for the personal number before deploy.
- Never promote a client photo into the `hero-background` / `cta-background` slots.
- No readable license plates or privacy-sensitive photos.
- Never use default Tailwind blue/indigo as primary — use `#1852D4` only.
- No `transition-all`.
- Follow the tiered screenshot rule above — don't stop after one pass on a *gated template
  page*; a single round + click-through is correct for clones.
- Do NOT publish any SneakPeek® accuracy percentage.
- Do NOT publish any certification claims — none confirmed.
- Twitter/X link must not appear anywhere on the site.

## Git Discipline — FROZEN
- Commit/push only when asked; branch first if on the default branch.
- Rename a service/city → update its filename, all hrefs, nav/footer labels, schema,
  title/meta, and breadcrumb together.
- Three-command pre-commit check, no exceptions: `git status`, `git branch`,
  `git remote -v` (the client repo, NOT nexor-template).
- Logical commit separation: CLAUDE.md → own commit; brand_assets → own commit; page
  builds grouped by phase. Never mix client-layer decisions with build work.
- Commit assets immediately on placement (their own commit).
- Set the canonical host (www.surepointelab.com) as Vercel **Primary on day one**, not at launch.
- Submit the sitemap to GSC as the full canonical URL. Indexing order: services → Pharr →
  McAllen → remaining cities → about. ~10–12 URL inspections/day; spread across days.
  Re-check the homepage canonical in GSC 3–5 days post-launch.

---

## Active Blockers

**Launch-blocking:**
- GHL contact form embed code (confirmed coming)
- GHL chat widget script (confirmed coming)
- GHL external tracking script (confirmed coming)
- GHL review widget embed code (confirmed coming)
- og-image — `brand_assets/og-image.jpg` (1200×630; create before launch)
- Hero video raw clip (confirmed coming; build with static hero first, swap on delivery)

**Backfillable (build against placeholders, swap in one pass):**
- Hero background photo (`brand_assets/hero-background.*`)
- CTA background photo (`brand_assets/cta-background.*`)
- All content / body photos (per photo tier allocation above)
- Staff names and roles (if client decides to add)
- priceRange (for JSON-LD only — never in copy)
- Warranty / guarantee terms
- Official tagline
- Experience framing exact wording (confirm "25 years" is personal/team claim)
- Owner personal phone number (record here only for suppression — must never appear on site)

**Pre-build structural work (Code does this before any page builds — confirmed by Prompt 0 audit):**
- Branch off main before any commit (main is the default branch — branch first)
- Commit CLAUDE.md + template-doc deletions (CLAUDE-SKELETON.md, TEMPLATE-SPEC.md) as
  their own commit on the new branch
- Drop `brand_assets/logo.png` in and verify brand.css tokens match this file's palette
  before any recolor pass
- Rename 6 template service stubs to real slugs (blood-work-lab-testing.html, etc.)
- Rename 6 template city stubs (city-one…six.html) to real slugs; CREATE 2 new city pages
  (alamo.html, donna.html) from the McAllen template — they do not exist on disk
- Site-wide domain sweep: replace all `https://yourbusiness.com/` with
  `https://www.surepointelab.com/` across all 15 HTML files + sitemap.xml + robots.txt
- Update sitemap.xml from 6 city entries to 8
- WORKFLOW.md does not exist in this repo — the copy methodology reference in CLAUDE.md
  points to SEO-CONTENT-PROMPT.md (present at 5.5 KB), which is correct; no action needed

**Nothing blocking the build structure.** All strategic decisions are locked.
CLAUDE.md is ready for Code.
