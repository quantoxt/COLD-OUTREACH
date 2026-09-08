# AGENTS.md — COLD-OUTREACH landing-page rebuilds

## Job
Rebuild outdated plumber landing pages (`NN_Name/index.html`) from scraped resources
(`NN_Name/_internal/resources/`), for cold-email outreach. One project at a time.

## Locked design system (do not deviate without being asked)
- **Same design + Airbnb + hyperminimalism**: Revolut component language
  (pill buttons 9999px, generous 14px/32px padding, zero shadows, flat surfaces),
  Inter Tight display (500, tight tracking) + Inter body,
  hyperminimal layout (one idea per section, 128px section rhythm, max 2 colors),
  Airbnb inflection (warm, hospitable copy and imagery).
- **Accent color**: always the original site's primary CTA color, extracted from
  its real `styles.css`/theme CSS (fetch it, count hex frequency, eyeball for
  false positives like `#beauty_prod` ID selectors). Ink `#191c1f`, paper white.
- **Stack only**: single `index.html` — Tailwind CDN (v4 browser), Google Fonts,
  Lenis (CDN). No build step, no other frameworks.

## Variety rule (sites must NOT all look the same)
- The skeleton order (§Page skeleton) and quality bar (Lenis rules, image rules,
  sticky nav, mobile-first, validation) are fixed. The VISUAL TREATMENT varies
  per client — study the screenshots of the original site and borrow its
  distinctive tokens:
  - hero treatment (light minimal vs full-bleed duotone photo band),
  - iconography (inline-SVG ticks vs line-icon cards vs badge chips),
  - brand devices (logo strips, accreditation cards, checklist bands),
  - footer character (minimal vs rich navy with link columns).
- Default to the Same+Airbnb+hyperminimal base, then layer the client's own
  tokens on top so each rebuild feels like *them*, just modernized.
  If the original has no distinctive tokens, stay close to base.

## Page skeleton (in order)
1. Sticky frosted nav (`sticky top-0 z-50`, `backdrop-blur`, hairline border) —
   logo, section links, tap-to-call pill, hamburger on mobile.
2. Hero — badge, display headline, sub, dual CTA (call primary + quote ghost).
   Side-by-side image ONLY for portrait-safe photos, capped
   (`aspect-square`, `max-h`, `object-top`). Ultrawide slider images with baked-in
   text go full-width at native ratio (e.g. `aspect-[21/9]`), never cropped.
3. Dark emergency strip with full-size badge, white pill CTA.
4. Services — alternating image/text rows when photo assets exist; checkmarked
   grid with inline-SVG ticks in accent color when they don't.
5. Why-us — credential list; trust-logo composites go to the footer, full-bleed
   at natural ratio.
6. Testimonials (only real scraped quotes, never invented).
7. Map (Google `maps?q=…&output=embed` iframe) + real street address.
8. Full-bleed dark quote form (name, email, phone, postcode, message) —
   FRONT-END ONLY (validation + confirmation state, no backend). Say so every time.
9. Minimal footer — copyright, address, phones, Gas Safe reg where present.

## Lenis rules (hard-won — follow exactly)
- NEVER `scroll-smooth` on `<html>` alongside Lenis.
- `new Lenis({ lerp: 0.1, smoothWheel: true, wheelMultiplier: 1.0, touchMultiplier: 1.5 })`.
- Include the Lenis CSS guards; anchor offsets must clear the sticky bar (`-72`);
  mobile menu auto-closes on navigation; respect `prefers-reduced-motion`.

## Image rules
- Scrapling `Fetcher` cannot download binaries — download images with `httpx`.
- White/transparent logos (check by viewing!) go on dark chips; circular photos
  render as circles; credential/logo composites are NEVER `object-cover` —
  always full at natural ratio.
- White/light icon PNGs are invisible on light sections — use accent chips or
  inline SVGs. Never invent accreditation logos (esp. Which?/Gas Safe).
- After every edit: validate tag balance and verify each referenced image file
  exists on disk.

## Scrape notes
- Per project: `texts.json` + `links.json` + `images.json` + `raw.html` +
  `images/` + `images_manifest.json`.
- Expect: `data:` placeholder URIs, hotlink-blocked images, 403s → retry with
  `StealthyFetcher(..., solve_cloudflare=True)`; if images still fail, write
  `_internal/resources/NOTE.md` with manual steps, never silently skip.
- A quick manual glance at the live site beats more scraping (real phone numbers
  hide in carousel overlays, addresses, review badges, form fields).

## Process rules
- Ask brand inspo + style picks before building (default: same system).
- Copy is the client's real copy; fix typos silently only if trivial.
  Phone/email CTAs use `tel:`/`mailto:` throughout (quote buttons may pre-fill subjects).
- The agent cannot render pages — user screenshots are the QA loop.
- **After each `index.html` build, return its ABSOLUTE path** so the user can
  open it in a browser.
- Commit + push to `main` after each build (`gh` auth: quantoxt).
- `.venv/` and junk are git-ignored — never commit them.
