# Rebuild Playbook (learned from No. 1)

## Scrape layer
- Scrapling `Fetcher` can't download binaries — use `httpx` for images, always.
- Expect junk: `data:` placeholder URIs, hotlink-blocked images, 403 bot-blocks. Record and move on.
- Color tokens live in the site's linked `styles.css`, not inline — fetch it, count hex frequency.
  Eyeball top hits for false positives (e.g. `#beauty_prod` ID selectors read as `#bea`).
- Resources per project: `texts.json` + `links.json` + `images.json` + `raw.html` +
  downloaded `images/` + `images_manifest.json`.

## Build layer (bake in from the first draft)
- Stack: Tailwind CDN (v4 browser), Google Fonts, Lenis.
- Lenis rules: NEVER `scroll-smooth` on `<html>` with Lenis; use `lerp: 0.1` mode
  (not `duration`); include Lenis CSS guards (`lenis-smooth`, `height: auto`).
- Hero: side-by-side grid on desktop; image in capped frame
  (`aspect-square`, `max-h`, `object-top`) so stock portraits can't blow up.
- Icons from old sites are often white/light PNGs — plan amber chips or inline SVGs.
- Sticky frosted nav (`sticky top-0`, `backdrop-blur`, hairline border) + hamburger
  menu on mobile; anchor scroll offset must clear the bar (~-72px).
- Quote form + map block included by default.
- Mobile-first throughout: tighter section rhythm, single-column form
  (`grid-cols-1 sm:grid-cols-2` + `sm:col-span-2`), full-width stacked CTAs,
  shorter card/map/hero images, compact phone pill.
- After edits: validate tag balance + verify every referenced image exists on disk.

## Process
- Agent can't render pages — user screenshots are the QA loop.
- Quick manual glance at the original site beats more scraping: real street address,
  review badges, quote-form fields.
- Ask brand inspo + style picks before building.
- Quote form is demo-only (front-end validation + confirmation state, no backend).
  State this plainly; offer `mailto:` fallback only if asked.
- Brand accent: keep the original site's primary CTA color as the single accent
  (hyperminimalism: max 2 colors).
