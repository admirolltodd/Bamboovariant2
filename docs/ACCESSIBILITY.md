# Accessibility Notes — Variant 2

Observations only. No layout or content changes were made to `index.html`
as part of this pass.

## Already in good shape

- `lang="en"` set on the page.
- A working skip-to-content link (`.skip`, targets `#main`), visible on
  focus.
- The scrolling marquee ticker (`.marquee`) is marked `aria-hidden="true"`
  since it repeats content already available elsewhere on the page —
  correct treatment for a decorative/redundant element.
- The mobile nav toggle button has `aria-expanded` and `aria-controls`
  wired up and kept in sync by the inline script.
- `@media (prefers-reduced-motion: reduce)` disables `scroll-behavior` and
  the marquee's scrolling animation.
- No forms exist on this page, so form labeling is not applicable.

## Observations for future, deliberate fixes

- **Focus visibility.** The only explicit `:focus` style in the page is on
  `.skip`. Interactive elements elsewhere (`.btn`, `.navlinks a`,
  `.location .actions a`) rely on the browser's default focus ring.
  Consider adding a visible `:focus-visible` style, especially for buttons
  that sit on the red (`--red: #df1f26`) or black (`--ink`) backgrounds
  where a thin default outline may be hard to see.
- **Heading level skip.** The footer uses `<h4>` ("Explore", "Locations")
  with no `<h3>` present anywhere on the page. Not a functional bug, but a
  screen-reader heading-list reader will see a level jump. If this is ever
  revisited, changing those two footer headings to `<h3>` would be a
  low-risk, isolated fix (not attempted in this pass, since it edits
  existing HTML).
- **Marquee readability.** `.marquee` scrolls continuously and its text
  content duplicates city names and taglines already present elsewhere on
  the page — good, since `aria-hidden="true"` means assistive tech skips
  it entirely rather than reading a never-ending ticker.
- **Color contrast.** White text on `--red: #df1f26` (used in `.orderbtn`,
  `.finalCta`, `.location .actions .order`) should be checked with a
  contrast tool for the smallest text sizes used in those areas before
  treating it as reliably AA-compliant. Large display headlines on this
  background are less likely to be an issue than small mono-font labels.

## Applied (near-zero-risk only)

No content or layout changes were made to `index.html`. The heading-level
and focus-visibility observations above were left as documented
recommendations rather than applied, since editing existing `<style>`/HTML
in `index.html` falls outside this pass's scope of "infrastructure and
documentation only."
