# Prosperity Pathways AP Foundation — Site Conventions

Static HTML/CSS site. No build step, no framework. Hosted on GitHub Pages, custom domain `prosperitypathwaysap.org`.

## Every new page MUST include

Copy an existing page (e.g. `contact.html`) as the starting point rather than writing from scratch. Every page needs:

- `<meta name="format-detection" content="telephone=no, date=no, address=no, email=no">` in `<head>` — prevents iOS from styling the EIN as a blue link
- The Givebutter script in `<head>`
- The Cloudflare Web Analytics script as the last thing before `</body>`:
  ```html
  <script type='module' src='https://static.cloudflareinsights.com/beacon.min.js' data-cf-beacon='{"token": "5867e298466c48e295efdd9d15eae82a"}'></script>
  ```
- The standard `<header class="nav">` including the `.nav-toggle` hamburger button and its script
- The `.hero` section with the `hero-contours` SVG
- The standard `<footer class="footer">`
- If the page has an `<aside>` sidebar nav, use the `.side-h-toggle` / `.side-list-wrap` accordion pattern and include its script

## CSS: critical gotcha

`.container` sets `padding: 0 32px`. Any class applied to the *same element* as `.container` must NOT use shorthand `padding` — shorthand with 2–3 values sets left/right to `0` and silently overwrites the container's side padding, which breaks mobile layout.

Always use `padding-top` / `padding-bottom` separately on these classes:
`.hero-inner`, `.crumbs-inner`, `.layout`, `.footer-inner`, and any future class paired with `.container`.

This bug has been introduced three times. Check for it.

## Links

Internal links use clean URLs with a leading slash and **no `.html`** — e.g. `href="/our-story"`, `href="/donate"`, `href="/"` for home. GitHub Pages resolves these automatically.

Do NOT strip extensions from asset paths (`site.css`, `assets/*.svg`) — those are files, not pages.

## Branches

- `main` — the live site
- `maintenance` — a standalone holding page. Its `index.html` is intentionally minimal (single nav link, simplified footer, no scripts). **Do not apply site-wide changes to this branch.**

## Content rules

- **Never publish student names, or any data identifying which students received funding.** These are minors and the information reveals financial need. Impact numbers only (e.g. "17 students, 28 exams, $2,520").
- Don't name partner schools publicly without confirmation from the school.
- The organization currently funds **AP exam fees only**. Do not describe prep materials, study resources, or mentorship as current services — those are future goals and belong only in "The Road Ahead" framing.
- Use HTML entities `&mdash;` and `&middot;` rather than literal `—` and `·` characters, to avoid encoding corruption.

## Design tokens

Defined as CSS variables in `site.css`. Use the variables, don't hardcode hex values.
Navy `--navy-800: #1B3A5C` · Gold `--gold-600: #B8860B` · Fonts: Merriweather (serif, headings), Source Sans 3 (sans, body).
