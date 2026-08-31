# Content Guide — Variant 2

Practical rules for editing this variant's content without breaking its
single-page design.

## Menu content

- The menu preview lives in the `<div class="menuGrid">` block in
  `index.html` — six `article.menuCard` items, each with a dish name, a
  short description, and a category label (e.g. "Specialty roll"). This is
  explicitly a **preview**, not the full menu.
- Do not add prices — the page's own copy already tells visitors pricing
  lives on the ordering platform (see `.menuNote`).
- Existing dish names (Crack Roll, Godzilla Roll, Mt. Fuji Roll, etc.) are
  already confirmed by the page's own content. If you add a new preview
  card, only use a dish name you can confirm elsewhere (menu board photo,
  another variant's verified menu copy, or the ordering platform) — don't
  invent one.

## Location content

- Location details live in the `<div class="locationGrid">` block —
  city name, phone number, a "Call" link and an "Order" link per location.
- **No street addresses are shown.** Keep it that way unless the site owner
  asks for addresses to be added — this looks like an intentional part of
  this variant's minimal, high-contrast layout rather than a gap.
- Each location's "Order" link points directly to that location's own
  ordering-system URL, opened in a new tab. Never point one location's
  Order link at another location's URL or a shared/generic ordering page.

## Photography

- Do not invent a dish name for a photo used outside the menu preview
  cards (hero image, photo band, story image). Use the same generic,
  descriptive alt text style already on the page (e.g. "Seared ahi tuna
  sashimi", "Bamboo dining room and sushi bar") unless a specific dish name
  is already confirmed by existing copy.

## Voice and tone

Existing copy is short, punchy, and uses sentence fragments for headlines
("Fresh. Fast. Local.", "Bar heat. Grill heat.", "Cut. Roll. Serve."). Body
copy stays to one or two short sentences per block. New copy should match
that density — this design relies on large type and generous whitespace,
and long paragraphs will overflow the fixed-height feature/location cards.
