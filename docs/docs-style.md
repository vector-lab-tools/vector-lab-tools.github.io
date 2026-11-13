# Vector Lab tool page — docs style

Conventions for a tool's own GitHub Pages site. Each tool hosts a single-page (or small multi-page) site in its own repo under `docs/`, served by Pages from `main` `/docs`. The hub at vector-lab-tools.github.io links to these; it does not host per-tool pages. Copy the tokens and patterns below so the pages read as one family.

Reference implementation: <https://vector-lab-tools.github.io/LLMbench/> (source in vector-lab-tools/LLMbench, `docs/index.html`). View-source it for anything not spelled out here.


## Build

- A single hand-written static `index.html`: HTML, one inline `<style>`, one short inline `<script>` for the theme toggle. No Jekyll, no theme, no framework, no build step. Pages serves the file as written.
- Pages source: branch `main`, folder `/docs`. Enable with:
  ```
  gh api -X POST repos/vector-lab-tools/<repo>/pages -f "source[branch]=main" -f "source[path]=/docs"
  ```
- The docs page takes its type and palette from this note, not from the tool's own app (globals.css / Tailwind). The app and the docs page are separate design surfaces. Pulling the app's fonts or neutrals into the docs page is the most common divergence.


## Type stack

One Google Fonts `<link>` with `preconnect` and `display=swap`.

- Display (hero, h1, h2, h3): **Cormorant Garamond**
- Body: **Source Serif 4**
- Eyebrows, labels, code, captions: **IBM Plex Mono**


## Colour tokens

Copy verbatim. Change only the accent group per tool.

```css
:root{
  --bg:#f6f2e9; --surface:#fffdf8; --surface-alt:#efe7d8;
  --ink:#141518; --muted:#5b5d66;
  --accent:#9a2d2d; --accent-hover:#7a2222; --accent-text:#8a2727; --on-accent:#fff;
  --rule:#e2d9c8;
  --serif:"Source Serif 4",Georgia,serif;
  --display:"Cormorant Garamond",Georgia,serif;
  --mono:"IBM Plex Mono",Menlo,monospace;
  color-scheme:light;
}
```

The neutrals (`--bg`, `--surface`, `--surface-alt`, `--ink`, `--muted`, `--rule`) stay fixed across tools. The accent is the one per-tool token: set `--accent`, `--accent-hover`, `--accent-text` (a darkened accent for small type on cream) and `--on-accent` from the tool's own colour. LLMbench uses burgundy; other tools pick their own.

Give `body` an explicit `background: var(--bg)`.

Dark mode is defined twice, with the same overrides each time (dark ground around `#0d0b12`, a lighter accent):

```css
@media (prefers-color-scheme: dark){
  :root:not([data-theme="light"]){ /* dark overrides */ }
}
:root[data-theme="dark"]{ /* same dark overrides */ }
```

The media query follows the operating system. The attribute selector lets the toggle force a theme against the OS setting.


## Page structure

Order on the landing page:

1. **Sticky header** (`backdrop-filter: blur`). Wordmark left; section anchor-nav plus the theme-toggle button (moon/sun SVGs) right.
2. **Hero**, two columns on desktop, one on mobile. Left: a mono eyebrow (`Vector Lab · a research instrument`), an `h1` wordmark in Cormorant Garamond with one word emphasised in the accent, a one-line lede, a sub of about 40 words, then CTA buttons. Right: the tool's strongest screenshot, framed. A visualisation tool may lead with its own image or a live canvas instead of a screenshot.
3. **Numbered sections.** Each opens with a mono eyebrow numeral, then the heading: `<p class="num">01 · About</p>` above an `h2`. Typical run: About, a feature tour, a worked example, Setup.
4. **Footer.** A `part of Vector Lab` text link to the hub, licence, and the main nav links.

Wrap width about 1060px.

**Way back to the hub.** Every tool page links back to https://vector-lab-tools.github.io/ in three places, so one is always on screen:

1. A `← Vector Lab` breadcrumb in the sticky header, top-left, above the tool wordmark. Small mono, uppercase, muted, accent on hover. It is a separate link from the wordmark: the wordmark goes to the docs home (`#top` on a single-page site, `index.html` on a multi-page one), and the breadcrumb is the only link that leaves the tool. On a multi-page site the breadcrumb goes on every page, not only the index, since readers arrive at deep pages from search. Set `white-space: nowrap` on the wordmark, or a long name breaks onto two lines at 375px; check at phone width.
2. The hero eyebrow's "Vector Lab" made a visible link, since it already names the family.
3. The footer link.

Never put the hub link in the main nav row: on mobile it either overflows or is hidden, exactly where a reader is most lost. Use the text breadcrumb, not an icon, as the baseline; a tool that shows the parent mark may add it, but not every tool does.

Each tool keeps its own wordmark and glyph; that is its identity. Parent references are plain text links to the hub. The hub is the one surface that carries the family mark, so tool pages do not inline the parent glyph.

If an app bundles a copy of the Vector Lab mark (for a "Part of Vector Lab" badge in the app chrome, say), use the files on the hub:

- `assets/images/logo-mark.svg` for the light-theme asset.
- `assets/images/dark/logo-mark.svg` for the dark-theme asset.
- `assets/images/logo-mark-small.svg` and `assets/images/dark/logo-mark-small.svg` for small sizes. Geometry is identical to the main mark; the small variant exists only so tools wanting a dedicated small-size file have one to reference. The mark is three polygon beams, not strokes, so it holds its sharpness at any size.
- `assets/images/favicon.svg` for the browser favicon, theme-aware via a `@media (prefers-color-scheme: dark)` block.

The mark is an inverted triangle built from three overlapping beams in three slightly different blues (electric #1a1aff, purple-blue #4a2aff, cyan-blue #1a6aff; the dark palette shifts each one lighter). The outer corners mitre into sharp triangle points; the inner edges extend past each mitred corner into the next beam's area, recursing around the triangle. The viewBox is `0 0 100 100` for every variant.

**Caveat for apps with a manual light/dark toggle.** An `<img>`-loaded SVG resolves `prefers-color-scheme` against the operating system, not the embedding document, so the theme-aware inline-style favicon only tracks an app's theme if that app follows the OS preference. An app with a manual toggle should use the dark-asset swap pattern instead: ship both `logo-mark.svg` and the `dark/logo-mark.svg` sibling and swap the `src` attribute when the user toggles. The hub carries both for this reason.

CTA buttons are pills: the primary one is filled with the accent (`Open the app`), the rest outlined.


## Screenshots

- Full-resolution PNG in `docs/screenshots/`.
- 1600px WebP thumbnails in `docs/screenshots/web/`:
  ```
  cwebp -q 82 -resize 1600 0 in.png -o web/out.webp
  ```
  `cwebp` is at `/opt/homebrew/bin/cwebp`. ffmpeg and sips do not encode WebP.
- Markup: the page loads the WebP; clicking opens the full PNG.
  ```html
  <figure>
    <a href="screenshots/NAME.png">
      <img src="screenshots/web/NAME.webp" loading="lazy" width="1600" height="1000" alt="…">
    </a>
    <figcaption>…</figcaption>
  </figure>
  ```
- Frame: border, rounded corners, soft shadow on the `<a>`. Caption beneath in `--mono`, small, `--muted`.
- Always set `width`/`height` to reserve space and stop layout shift.


## Setup and API keys

The section users stall on. Keep it the longest, and keep it concrete.

- One section, per-provider **cards** in a grid. Not collapsed; collapsing hides what people came for.
- Each card: where the key comes from, its prefix, a free / paid / local badge, and the one gotcha for that provider.
- A small mono pill carries the badge. Wording is standard across tools: `free`, `paid`, `local`.
- For a local model path (Ollama), give the exact command with a copy button, and the Safari caveat (Safari blocks the browser-direct localhost call; Chromium-family and Firefox allow it):
  ```
  OLLAMA_ORIGINS="https://<app-origin>,http://localhost:3000,http://127.0.0.1:3000" ollama serve
  ```
- Keep a hosted-keys subsection only while the tool uses hosted providers. A tool with no keys drops the section and keeps a short "Run it" block for its env vars and deploy command instead. Do not pad a configuration section that has nothing in it.
- Promoting "Setup" or "API keys" to a top-bar destination is need-driven. Do it when keys are the tool's pain point.


## Theme toggle

A short inline script sets `data-theme` on `<html>` from `localStorage`, and the toggle button flips and saves it.

- A **light-default** page can run the script at the end of `<body>`.
- A **dark-default** page runs the script **inline in `<head>`**, before any CSS paints, or the first paint flashes light on every load. Default the CSS to dark under `:root` as well, so a page with JavaScript off still opens dark.


## Pitfalls

- An asset path that points outside `docs/` (for example `../public/favicon.svg`) 404s on Pages. Keep every reference relative to `docs/`, or inline a `data:` URI favicon.
- Heavy full-resolution PNGs make the page slow. Use the WebP thumbnails above.
- No Jekyll is involved. Add `docs/.nojekyll` only if a directory with a leading underscore is introduced, which Pages' Jekyll would otherwise strip.
- Two-column hero collapses to one column on mobile. A wide `<pre>` scrolls on its x-axis rather than overflowing the page. A provider-card grid wraps to fewer columns on a phone.


## Multi-page sites

For a site of several pages, put the whole stylesheet in one `docs/style.css` that every page links with `<link rel="stylesheet" href="style.css">` (relative, no leading slash), rather than inlining it on each page. Duplicate the short header and footer HTML per page, and mark the current page's nav link active. The theme-toggle script stays inline on each page.


## Citation

The *Vector Theory* article is the preferred citation for every tool; the tool's own Zenodo DOI is the second reference.

**CITATION.cff.** Keep the software metadata at the top level, including the tool's Zenodo concept DOI under `identifiers` (four tools currently omit it), and add this block so GitHub's "Cite this repository" offers the article first. The hub's file is the reference copy.

```yaml
preferred-citation:
  type: article
  authors:
    - family-names: Berry
      given-names: David M.
      affiliation: University of Sussex
      orcid: "https://orcid.org/0000-0002-7737-5586"
  title: "Vector Theory: Epistemology, Political Economy, and Probabilistic Computation"
  journal: "Philosophy & Technology"
  year: 2026
  volume: 39
  doi: 10.1007/s13347-026-01162-w
  url: "https://doi.org/10.1007/s13347-026-01162-w"
```

Check the ORCID against its checksum before any release; an invalid one makes Zenodo skip the deposit without an error. After the first release that carries this block, check the new Zenodo record still describes the software and not the article.

**In the app.** Put a cite line in the About panel and in every export (CSV, JSON, PDF, image captions), so it travels with any figure made from the tool:

"Cite: Berry, D. M. (2026) 'Vector Theory: Epistemology, Political Economy, and Probabilistic Computation', Philosophy & Technology, 39. doi:10.1007/s13347-026-01162-w. Tool: <name> v<version>, doi:<concept DOI>."

## In-app conventions

The rest of this note covers docs pages. These cover the apps themselves. Reference implementation: vector-lab-tools/LLMbench commits 168dfe0 and 6db914a.

- **Help** opens as sidebar panes, with the header and footer pinned.
- **Settings** sits centred at no more than 90vh; only the middle scrolls, and its options sit in a row of their own.
- **Every modal** closes on a backdrop click and on Escape.
- **Settings edits a draft.** Closing with unsaved changes asks Keep editing / Discard / Save.
- **A saved model is reconciled on load.** If a provider has retired it, the app falls back to that provider's default rather than failing.

## Voice

Page copy follows the house rules:

- No em dashes. Use commas or restructure.
- British spelling.
- Documentary register. State what is the case.
- No aphoristic or mirrored closers, no `Not X but Y`, no sentence that restates a paragraph's point at its end. End on the last piece of content.
- Avoid "legible/legibility" and "honest/honesty".

Funding acknowledgement, for LLMbench, Manifold Atlas, Vectorscope, Manifoldscope, Theoryscope and Diffusion Atlas (not Vectorography). Use it verbatim in the docs page footer, the README and any FAQ history entry; in HTML write the ø as `&oslash;`: "Built at Copenhagen Business School, Denmark, during an Otto Mønsted Visiting Professorship in 2026. The support of the Otto Mønsted Fond (grant 25-12-1849) is gratefully acknowledged."

Wherever a page tells readers how to report a problem, use this line, with the tool's repository linked: "If it is not on this page, open an issue on the tool's repository to report the problem. If you have a fix, a pull request is welcome."
