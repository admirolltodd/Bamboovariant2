# Project Structure — Variant 2

This reflects the actual repository layout. It is documentation only; no
files were moved or renamed to produce this listing.

```
/
├── index.html            # The entire site: one page, inline <style> and inline <script>
├── 404.html              # Custom not-found page (new — has its own small isolated <style>)
├── robots.txt
├── sitemap.xml
├── netlify.toml
├── README.md
├── images/
│   ├── awards/            # Community's Choice / Best of Florida award graphics
│   ├── brand/              # Logo files
│   ├── food/                # Dish photography
│   ├── gallery/             # Storefront and dining-room photography
│   ├── menu/                 # Menu board photographs
│   └── press/                # Press clippings
└── docs/                  # This documentation set
    ├── PROJECT-STRUCTURE.md
    ├── ASSETS.md
    ├── CONTENT-GUIDE.md
    ├── DEPLOYMENT.md
    ├── SEO.md
    ├── ACCESSIBILITY.md
    └── MAINTENANCE.md
```

## Notes

- **There is no `css/` or `js/` directory.** All styling lives in a single
  `<style>` block and all interactivity in a single `<script>` block inside
  `index.html`. This is different from Variant 1 and Variant 3, which use
  external stylesheets — it's a deliberate characteristic of this variant,
  not an omission, and this infrastructure pass did not restructure it.
- `404.html` cannot `<link>` to a shared stylesheet because none exists. It
  carries its own small, isolated `<style>` block with just the design
  tokens and header/footer chrome needed to look consistent with
  `index.html` — see the comment at the top of `404.html` for why.
- There are no separate `menu.html` / `locations.html` / `story.html`
  pages in this variant; those topics are sections within `index.html`
  reached via in-page anchors (`#menu`, `#story`, `#locations`).
