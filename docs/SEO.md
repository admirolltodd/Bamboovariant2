# SEO Recommendations — Variant 2

This variant's HTML was **not modified** by this infrastructure pass, per
the project's non-destructive rules. Everything below is a recommendation
for a future, deliberate content change — not something already applied.

## Current state (as of this audit)

- `index.html` has a unique `<title>` and a `<meta name="description">`.
- No `<link rel="canonical">`.
- No Open Graph (`og:*`) or Twitter Card (`twitter:*`) meta tags.
- No JSON-LD structured data.
- Favicon is set (`images/brand/bamboo-sushi-hibachi-logo.png`).
- Heading order has one notable gap: the footer uses `<h4>` for "Explore" /
  "Locations" labels with no `<h3>` anywhere on the page — not an SEO
  penalty by itself, but worth knowing if headings are ever audited (see
  `docs/ACCESSIBILITY.md`).
- `robots.txt` and `sitemap.xml` were added by this pass and are crawlable
  (new standalone infrastructure files, not existing page edits). Because
  this variant is a single page, the sitemap lists only `/`.

## Recommended (not applied) canonical tag

Add `<link rel="canonical" href="https://REPLACE-WITH-PRODUCTION-DOMAIN/">`
to `index.html` once a production domain is confirmed. Don't guess the
domain in the meantime.

## Recommended (not applied) Open Graph / Twitter Card tags

Using only facts already present in this repository:

```html
<meta property="og:type" content="restaurant">
<meta property="og:title" content="Bamboo Sushi Bar & Hibachi Express">
<meta property="og:description" content="Bamboo Sushi Bar & Hibachi Express on Florida's Emerald Coast. Sushi, hibachi, and three local locations in Crestview, Fort Walton Beach, and Niceville.">
<meta property="og:url" content="https://REPLACE-WITH-PRODUCTION-DOMAIN/">
<meta property="og:image" content="https://REPLACE-WITH-PRODUCTION-DOMAIN/images/food/seared-ahi-tuna-sashimi-emerald-coast.webp">
<meta name="twitter:card" content="summary_large_image">
```

No dedicated 1200×630 social-share crop exists in this repo today (see
`docs/ASSETS.md`); the hero image above is a placeholder choice, not a
confirmed social-share asset.

## Structured data — blocked on a missing fact, not a formatting choice

A `Restaurant`/`LocalBusiness` JSON-LD block normally needs a
`PostalAddress` per location. **This variant's `index.html` does not
display a street address for any of the three locations** (only city name
and phone number — see `docs/CONTENT-GUIDE.md`). Per this project's rule
against inventing business details, do not fabricate addresses to fill out
structured data. Two honest paths forward, for the site owner to choose:

1. Add street addresses to the visible page copy first (a deliberate
   content decision, out of scope for this infrastructure pass), then add
   full `Restaurant` structured data with `PostalAddress` per location —
   the same three addresses used in Variant 1 and Variant 3 are the
   correct ones if this is in fact the same three restaurants.
2. Or, if this variant intentionally omits addresses, ship a reduced
   `Restaurant` JSON-LD block using only name and `telephone` per location,
   omitting `address` entirely rather than guessing one:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Restaurant",
  "name": "Bamboo Sushi Bar & Hibachi Express",
  "servesCuisine": "Japanese",
  "location": [
    { "@type": "Place", "name": "Bamboo Sushi Bar & Hibachi Express - Crestview", "telephone": "+1-850-689-1391" },
    { "@type": "Place", "name": "Bamboo Sushi Bar & Hibachi Express - Fort Walton Beach", "telephone": "+1-850-200-4250" },
    { "@type": "Place", "name": "Bamboo Sushi Bar & Hibachi Express - Niceville", "telephone": "+1-850-678-0771" }
  ]
}
</script>
```

Either way, this is a decision for the site owner, not something this
infrastructure pass should decide by editing `index.html` on its own.

## Sitemap / robots

Both were added as new standalone files in this pass (not existing-page
edits). The sitemap lists only `/` because this variant is genuinely a
single page today — do not add `#menu`/`#story`/`#locations` as separate
sitemap entries; sitemaps list pages, not in-page anchors. Update
`REPLACE-WITH-PRODUCTION-DOMAIN` in both files together once a production
domain is confirmed.
