# Bamboo Sushi Bar & Hibachi Express — Variant 2 (Bright Black/White/Red Concept)

This repository is one of three parallel design concepts for the Bamboo
Sushi Bar & Hibachi Express website. **Variant 2 is the bright, high-contrast
single-page concept**: a stark white background, heavy black rules, and a
strong red accent, built as one long scrolling page rather than separate
subpages.

This README documents this variant only. It does not describe Variant 1
(multi-page usability concept) or Variant 3 (premium dark concept) — those
live in their own repositories.

## Design concept

- Bright white/black/red palette: `--white:#fff`, `--ink:#0b0b0b`,
  `--red:#df1f26`, with hard 1–2px black rules, drop-shadow "sticker"
  buttons (`box-shadow: Npx Npx 0 var(--ink)`), and a scrolling marquee
  ticker.
- Display type is **Archivo Black** (loaded from Google Fonts) for large
  uppercase headlines, body copy in **DM Sans**, and label/mono accents in
  **IBM Plex Mono** — all loaded via a single Google Fonts request in
  `index.html`.
- One page, four in-page sections (`#menu`, `#story`, `#locations`, plus the
  hero at `#top`) rather than separate HTML pages per topic.

## Page structure

This variant currently has a **single HTML page**:

| Page | File | Purpose |
|---|---|---|
| Home (everything) | `index.html` | Hero, two-sides feature grid, photo band, menu preview, story, locations, final CTA, footer |
| 404 | `404.html` | Custom not-found page (added as part of this infrastructure pass) |

In-page anchors: `#top` (hero), `#menu` (menu preview), `#story`,
`#locations`. There are no separate `menu.html`/`locations.html` pages in
this variant — everything lives on `index.html`.

## Running locally

No build step, no package manager. Serve the repository root with any
static file server, for example:

```
python3 -m http.server 8080
```

or

```
npx serve .
```

Then open `http://localhost:8080/`. The page depends on a live connection
to Google Fonts (`fonts.googleapis.com` / `fonts.gstatic.com`) for its
typography — offline preview will fall back to system fonts for headings.

## Primary directories

```
/
├── index.html          # The entire site: inline <style> and inline <script>, no separate CSS/JS files
├── 404.html            # Custom not-found page (new)
├── images/
│   ├── awards/
│   ├── brand/
│   ├── food/
│   ├── gallery/
│   ├── menu/
│   └── press/
├── docs/                # Infrastructure & production documentation (this pass)
├── robots.txt
├── sitemap.xml
└── netlify.toml
```

Unlike Variant 1 and Variant 3, this repository has **no `css/` or `js/`
directory** — every style rule and the small amount of interactive
JavaScript (mobile nav toggle, footer year) live inline inside
`index.html`'s `<style>` and `<script>` blocks. This pass did not extract
them into external files, since doing so would mean editing `index.html`
itself.

## Where content actually lives

- **Menu preview content** (six sample dishes with descriptions) is written
  directly into the `<div class="menuGrid">` block in `index.html`. It is
  explicitly a *preview*, not the full menu, and carries no prices — the
  page's own copy says pricing stays on the ordering platform.
- **Location content** is written directly into the `<div
  class="locationGrid">` block in `index.html`. Note: **this variant shows
  only the city name and phone number per location — no street address is
  displayed anywhere on the page.** Do not add addresses without checking
  with the site owner first; their absence appears to be a deliberate
  design choice for this concept (a cleaner "Call" / "Order" action pair
  per city) rather than an oversight.
- **Order links** are direct links to each location's own ordering-system
  URL (`menu-6161.orderexperience.net/...`), one per location in
  `.locationGrid`, opened in a new tab (`target="_blank" rel="noopener"`).
  There is no shared/generic ordering destination.

## JavaScript behavior

All inline in `index.html`'s closing `<script>` block:

- Toggles `hidden` on `#mobileNav` when `#menuToggle` is clicked, and keeps
  `aria-expanded` in sync.
- Closes the mobile nav again when a link inside it is clicked.
- Sets the footer's `#year` span to the current year.

There is no other client-side behavior (no analytics, no map embeds, no
third-party widgets) today.

## Deployment

Deployed as a static site on Netlify. See `docs/DEPLOYMENT.md` for the full
checklist. Publish directory is the repository root, no build command.
`netlify.toml` now carries caching and security headers — see that file and
`docs/DEPLOYMENT.md` for why the Content-Security-Policy explicitly allows
`fonts.googleapis.com`/`fonts.gstatic.com`.

## Production checklist

- [ ] Click every anchor nav link (`#menu`, `#story`, `#locations`) and
      confirm smooth-scroll lands on the right section.
- [ ] Click every "Call" and "Order" link for all three locations.
- [ ] Test the mobile nav toggle at a narrow viewport.
- [ ] Confirm Google Fonts still load (Archivo Black / DM Sans / IBM Plex
      Mono) — the CSP in `netlify.toml` must keep allowing
      `fonts.googleapis.com` and `fonts.gstatic.com`.
- [ ] Confirm `robots.txt` is served as plain text and `sitemap.xml` as XML.
- [ ] Confirm `404.html` renders for an unknown path and returns HTTP 404.

## Known limitations

- No Open Graph, Twitter Card, canonical link, or JSON-LD structured data.
  See `docs/SEO.md` for specific, non-destructive recommendations.
- No street addresses are shown for any location (see note above) — this
  was left as-is rather than "fixed," since it may be intentional.
- All CSS and JS are inline in `index.html`; there is no shared stylesheet
  for `404.html` to link to, so `404.html` carries its own small, isolated
  copy of the shared design tokens (see `docs/PROJECT-STRUCTURE.md`).
- No automated tests or link checker; verification is manual (see checklist
  above and `docs/MAINTENANCE.md`).

## Related repositories

- Variant 1 (multi-page usability concept) — separate repository.
- Variant 3 (premium dark, combined/final concept) — separate repository.
- `828bamboosushi` — production-engineering reference repository used to
  inform the infrastructure and documentation patterns in this `docs/`
  folder. Its page content and visual design are not part of this variant.
