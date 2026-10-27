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

Each tool keeps its own wordmark and glyph; that is its identity. Parent references are plain text links to the hub. The hub is the one surface that carries the family mark, so tool pages do not inline the parent glyph.

If an app bundles a copy of the Vector Lab mark (for a "Part of Vector Lab" badge in the app chrome, say), use the right variant for the display size:

- **42 px and above (header, hero, modal):** the four-path wireframe tetrahedron. `assets/images/logo-mark.svg` on the hub (stroke 2.6, theme-aware via inline style).
- **Below ~40 px (status bar, inline badge, favicon):** the filled silhouette. `assets/images/logo-mark-small.svg` on the hub. The interior edges of the wireframe collapse into a smudge under 32 px.

Both variants carry `viewBox 0 0 100 100` so dimensions behave the same across sizes.

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


## Voice

Page copy follows the house rules:

- No em dashes. Use commas or restructure.
- British spelling.
- Documentary register. State what is the case.
- No aphoristic or mirrored closers, no `Not X but Y`, no sentence that restates a paragraph's point at its end. End on the last piece of content.
- Avoid "legible/legibility" and "honest/honesty".
