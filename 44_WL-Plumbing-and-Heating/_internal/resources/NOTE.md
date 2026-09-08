# NOTE — manual handling required

The page copy and links scraped fine, but **none of the site's images could be
downloaded** (hotlink protection / dead URLs / bot-guarded CDN).

A human needs to handle this project manually:
1. Visit the live site in a browser.
2. Save the needed images (hero, services, badges, logo).
3. Drop them into `_internal/resources/images/` as `img_XX.ext`.
4. Append entries to `images_manifest.json` in the same format:
   `{"file": "images/img_XX.ext", "from": "<source URL>", "alt": "<alt>", "bytes": <n>}`.
5. Delete this NOTE.md once done.

Declared image URLs are preserved in `_internal/resources/images.json` for reference.
