# Maintenance Guide — Variant 2

Practical instructions for common future edits. No build tools, package
managers, or frameworks are involved anywhere in this workflow — everything
lives inline in `index.html`.

## Updating menu preview descriptions

1. Edit the relevant `<article class="menuCard">` block directly in
   `index.html` (inside `<div class="menuGrid">`).
2. Do not add prices — the page's own `.menuNote` copy already tells
   visitors pricing lives on the ordering platform.
3. Only use a dish name you can confirm (existing menu copy, a menu board
   photo, or the ordering platform) — don't invent one.

## Updating location information

1. Edit the relevant `<article class="location">` block inside `<div
   class="locationGrid">` in `index.html`.
2. This variant shows only city + phone (no street address) — keep that
   pattern unless the site owner asks for addresses to be added.
3. If phone numbers change, update both the visible `.meta` text and the
   matching `tel:` links (there are two per location: one in
   `.locationGrid`, one in the footer).

## Replacing hero photos

Replace the file referenced by `.heroVisual img` in `index.html` with a new
file in `images/food/` (see `docs/ASSETS.md` for naming convention). Give
the new file a new, descriptive filename rather than overwriting the old
one — `netlify.toml` caches everything under `/images/*` for a year, so
reusing a filename means returning visitors keep seeing the old photo until
their cache expires. Also update the `<link rel="preload" as="image"
href="...">` in `<head>` to match, since the hero image is preloaded by
filename.

## Adding gallery/photo-band images

Add the new file to the matching `images/` subfolder and reference it from
the relevant section (`.photoBand` or `.storyMedia`). Do not caption it
with a specific dish name unless that name is already confirmed elsewhere
(see `docs/CONTENT-GUIDE.md`).

## Updating ordering links

Each location's "Order" link in `.locationGrid` points directly to that
location's own URL on the ordering platform
(`menu-6161.orderexperience.net/...`). If a location's URL changes, update
it only in that location's `<article class="location">` block — do not
consolidate multiple locations onto one shared ordering URL.

## Testing mobile layouts

Resize the browser below 980px and then below 620px (the two breakpoints in
`index.html`'s inline `<style>`) and confirm:

- `.menuToggle` appears and `#mobileNav` opens/closes correctly.
- The hero, feature grid, photo band, menu grid, locations grid and footer
  all collapse to a single column at the appropriate width.
- The marquee ticker still scrolls (or stays static if
  `prefers-reduced-motion` is on).

## Validating sitemap changes

If this variant ever grows beyond a single page:

1. Add the corresponding `<url>` entry to `sitemap.xml`.
2. Validate the file is well-formed XML (e.g. `python3 -c "import
   xml.dom.minidom as m; m.parse('sitemap.xml')"`).
3. Confirm every URL in the sitemap actually resolves to a real page.

Until then, `sitemap.xml` should keep listing only `/` — do not add
in-page anchors like `#menu` as separate sitemap entries.

## Testing 404 routing

Visit an unknown path (e.g. `/does-not-exist`) on the deployed site and
confirm `404.html` renders and the response status is 404 (check with
`curl -I` or browser dev tools). If the shared design tokens in
`index.html`'s `<style>` block change (colors, fonts), update the isolated
copy at the top of `404.html`'s `<style>` block to match — see the comment
there for why the two can't simply share one stylesheet today.

## Deployment checks

See `docs/DEPLOYMENT.md` for the full pre-deploy checklist.
