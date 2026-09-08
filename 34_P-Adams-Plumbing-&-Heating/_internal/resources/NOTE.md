# NOTE — manual handling required (images only)

The page copy and links scraped fine (via Cloudflare-solving stealth fetch),
but **none of the site's 20 images could be downloaded** (Cloudflare-guarded
CDN — the text/HTML loads, the image CDN does not).

A human needs to handle the images manually:
1. Visit https://padamsplumbingandheating.co.uk/ in a browser.
2. Save the needed images (hero, services, badges, logo).
3. Drop them into `_internal/resources/images/` as `img_XX.ext`.
4. Append entries to `images_manifest.json` in the same format:
   `{"file": "images/img_XX.ext", "from": "<source URL>", "alt": "<alt>", "bytes": <n>}`.
5. Delete this NOTE.md once done.

Declared image URLs are preserved in `_internal/resources/images.json` for reference.
