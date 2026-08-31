# Asset Guide — Variant 2

Documents where image assets live and how they're used. This does not
rename or move any existing file.

## Directories

| Directory | Contents |
|---|---|
| `images/brand/` | `bamboo-sushi-hibachi-logo.png` (used as favicon and in header/footer brand mark) and `bamboo-sushi-hibachi-logo-full.png` (currently unused by `index.html`) |
| `images/food/` | Dish photography used in the hero, "Two Sides" photo band, and menu preview area |
| `images/gallery/` | Storefront, signage and dining-room photography (the "Our Story" section uses `dining-room-interior-sushi-bar-menu-boards.webp`) |
| `images/menu/` | Photographs of physical menu boards (not currently placed on the single page) |
| `images/awards/` | Community's Choice and Best of Florida award graphics (not currently placed on the single page) |
| `images/press/` | Press clipping images (not currently placed on the single page) |

## Naming conventions already in use

Filenames are descriptive kebab-case. Unlike Variant 1, this variant's
`images/food/` folder does not carry `-800w` responsive-size suffixes on
every file (e.g. `chicken-shrimp-steak-hibachi.webp`, `sunset.webp`,
`volcano.webp` are single files, not paired with a smaller variant) — treat
that as this variant's current convention rather than a gap to "fix" by
renaming.

## Assets that should not be renamed

Every file currently referenced by an `<img src="...">` or `<link
rel="icon">` in `index.html` or `404.html`. Renaming any of them requires
updating every place that references that filename.

## Content safety

Do not caption or rename an image with a specific dish name (e.g. "Volcano
Roll", "Spicy Tuna") unless the existing alt text or page copy already
names it. The menu preview cards in `index.html` do name specific dishes
(Crack Roll, Godzilla Roll, Mt. Fuji Roll, etc.) — those names come from
the page's own existing copy and are already verified by that copy; that
does not extend to unrelated gallery/food images whose filenames merely
resemble a dish name (`sunset.webp`, `volcano.webp`) without matching alt
text confirming it.

## Where future optimized images should go

Add new photography into the existing category folder that matches its
subject (`images/food/`, `images/gallery/`, etc.) rather than creating new
top-level image directories.
