# Project Reference Notes

Running log of observations, decisions, and things to revisit as we build templates.

---

## Page Cleanup Methodology

This is the repeatable process for every page. Follow in order.

### Phase 1 — Clone & Backup
1. HTTrack clone the live page into `cloned-pages/<page-name>/` — **never edit this folder**
2. Copy `cloned-pages/<page-name>/index.html` → `html-templates/<page-name>/index.original.html` — **locked backup, never edit**
3. Copy again → `html-templates/<page-name>/index.html` — this becomes the **clean reference** being built

### Phase 2 — Inventory the source
1. Count total lines, image references, and `<link>` / `<script>` tags
2. List all CSS dependencies (IDs + filenames) → log in reference.md
3. List all JS dependencies → decide keep/remove per the general rules
4. Log findings in reference.md

### Phase 3 — Strip scripts
Remove in this order (do not remove anything not listed without discussion):
- HTTrack injected comment (line 1) and `<meta http-equiv="content-type">` (line 2)
- Google Tag Manager (consent block + GTM loader)
- Cookiebot
- Blackbaud `og-web-loader`
- WPML cookie JS + extra data script
- Gravity Forms JS hook system (`var gform; gform||...` block)
- Google reCAPTCHA v3
- WPML legacy dropdown JS
- Any other non-visual analytics/tracking scripts

**Rule: Never remove visual layout scripts or jQuery without explicit approval.**

### Phase 4 — Localize CSS
1. Download all `<link rel="stylesheet">` files to `assets/css/`
2. Flatten all delayed-load patterns (`loadCSS`, `preload` + `onload`) → simple `<link rel="stylesheet" href="assets/css/FILENAME">`
3. Check every CSS file for broken asset references:
   - **Icon fonts** — look for `url(path/to/fonts/...)` relative paths → convert to absolute URLs pointing to the live server
   - **Web fonts** — download `.woff2` files to `assets/fonts/` and patch `url()` references
   - **SVG background images** — look for `url('/wp-content/uploads/...')` → download SVGs to `assets/images/` and patch paths to `url('../images/...')`
4. Verify visually in browser side-by-side vs original before proceeding

### Phase 5 — Freeze clean version + create working copy
1. The completed `index.html` is now the **clean reference** — do not touch it further
2. `cp index.html index.working.html`
3. Create `assets/css/<page-name>-overrides.css` (empty stub with comments)
4. Add `<link rel="stylesheet" href="assets/css/<page-name>-overrides.css">` as the **last** CSS link in `index.working.html` only
5. All further HTML modifications go into `index.working.html`; CSS overrides go into `<page-name>-overrides.css`

### Phase 6 — Working modifications (in `index.working.html`)
- Replace Gravity Forms form blocks with plain HTML `<form>` matching the visual layout
- Remove any remaining WP-specific markup as agreed
- Update progress tracker in README.md and cleanup status table in reference.md

### Phase 7 — Elementor JSON export (future phase)
- TBD — process to be defined once working HTML is stable

---

### Known Asset Path Pitfalls (learned from home page)

| Problem | Root cause | Fix |
|---------|-----------|-----|
| Icon fonts render as random characters | Divi `divi-core.min.css` uses `url(core/admin/fonts/...)` — relative to WP server root | Patch to absolute URL: `url(https://truecare.org/wp-content/themes/Divi/core/admin/fonts/...)` |
| Heading/body fonts wrong weight | Child theme CSS uses `url('../truecare/fonts/...')` — correct on WP, broken locally | Download `.woff2` files to `assets/fonts/`, patch path to `url('../fonts/...')` |
| SVG chevrons render as colored blobs | CSS uses root-relative `/wp-content/uploads/file.svg` — not valid without a server root | Download SVGs to `assets/images/`, patch path to `url('../images/file.svg')` |
| A CSS file downloads as 0 bytes | Cloudflare bot protection blocks certain requests | Note in reference.md; check if visually critical. GF files are not critical since form is being replaced |

---

## Environment

| Key | Value |
|-----|-------|
| Codespaces base URL | `https://probable-bassoon-x566699qg52gxv.github.dev/` |
| Preview URL pattern | `https://probable-bassoon-x566699qg52gxv-<PORT>.app.github.dev/` |
| Workspace path | `/workspaces/tc-pillarpage-templates` |

---

## General Rules

- **Do not remove image links or asset URLs** — all external references to `truecare.org` must stay intact while building the functional prototype. We will swap in our own assets only when explicitly directed.
- **Do not remove any markup** without discussing it first.
- **Preserve all visual styling** exactly as the source — deviations only when directed.
- All changes go into `html-templates/<page-name>/` — the `cloned-pages/` source files are read-only.

---

## Brand Tokens (extracted from home page)

| Token | Value | Usage |
|-------|-------|-------|
| Primary teal | `#1b989a` | Links, primary buttons, CTAs |
| Primary pink | `#e41b7a` | All headings (h1–h6) |
| Orange accent | `#f98909` | Social share icons |
| Body text | `#646464` | Default paragraph color |
| Font family | `'Muli', sans-serif` | Body, inputs, textarea, select |
| H1 size | `45px` | |
| H2 size | `38px` | |
| H3 size | `32px` | |
| H4 size | `27px` | |
| H5 size | `23px` | |
| H6 size | `21px` | |
| Body font size | `19px` | |

---

## Home Page — Source Analysis

**File:** `cloned-pages/home/index.html`
**Lines:** 2,821
**Cloned from:** `truecare.org` via HTTrack (May 23, 2026)
**Original CMS:** WordPress 6.9.4 + Divi theme 4.27.6 + child theme `truecare`

### External CSS Dependencies (loaded from truecare.org)

| ID | File | Source |
|----|------|--------|
| `sbi_styles` | Instagram Feed plugin CSS | WP plugin |
| `ctshowcase-general` | Creative Team Showcase CSS | WP plugin |
| `wpml-legacy-dropdown-0` | WPML language switcher CSS | WP plugin |
| `et_monarch-css` | Monarch social sharing CSS | Elegant Themes plugin |
| `divi-ajax-filter-styles` | Divi Machine AJAX filter CSS | WP plugin |
| `divi-machine-styles` | Divi Machine CSS | WP plugin |
| `dwd-map-extended-styles` | Map Extended CSS | WP plugin |
| `algolia-autocomplete-css` | Algolia search autocomplete CSS | WP plugin |
| `dmach-carousel-css` | Divi Machine carousel CSS | WP plugin |
| `divi-style-parent-css` | **Divi theme core CSS** (`style-static.min.css`) | Theme — critical |
| `divi-style-css` | **TrueCare child theme CSS** (`style.css`) | Theme — critical |
| `mediaelement` | WP media player CSS | WP core |
| `gform_basic` | Gravity Forms basic CSS | WP plugin |
| `gform_theme_components` | Gravity Forms theme components | WP plugin |
| `gform_theme` | Gravity Forms theme CSS | WP plugin |

> **Note:** The two most critical stylesheets are `divi-style-parent-css` and `divi-style-css`. All visual layout depends on them. These are loaded from the live truecare.org domain — they will keep working in the prototype as long as the site stays live.

### External JS Dependencies

| Script | Purpose | Keep in template? |
|--------|---------|-------------------|
| Gravity Forms inline JS | Form hook system | Discuss |
| Google Tag Manager (`GTM-KGBRDSL`) | Analytics | Remove in final template |
| Cookiebot | Cookie consent UI | Remove in final template |
| WPML cookie JS | Language switcher cookie | Remove in final template |
| jQuery 3.7.1 (WP core CDN) | Base JS library | Keep — many things depend on it |
| WPML legacy dropdown JS | Language switcher | Discuss |
| Divi Machine grid JS | IE grid polyfill | Remove in final template |
| Google reCAPTCHA v3 | Form spam protection | Keep if form is kept |
| Blackbaud `og-web-loader` | Donation widget | Remove in final template |
| Five9 chat widget | Live chat | Remove in final template |

### Image References

- **Total image/src references:** 98
- All images point to `https://truecare.org/wp-content/uploads/...`
- These URLs will keep working in the prototype (site is live)
- When we swap assets, we will update paths to `assets/images/` local files

### Known Issues to Address Later

- [ ] HTTrack comment on line 4 — remove when we copy to `html-templates/`
- [ ] `<meta http-equiv="content-type">` added by HTTrack on line 5 — remove when copying
- [ ] `<link rel="pingback">` (line 16) — WP-specific, remove in template
- [ ] Multiple RSS/oEmbed `<link rel="alternate">` tags — WP-specific, remove in template
- [ ] Yoast SEO meta block — strip or simplify for template
- [ ] `document.documentElement.className = 'js'` script — small but harmless, keep for now
- [ ] GTM script block — keep functional in prototype, remove in final clean template
- [ ] Cookiebot script — keep in prototype (loads from external), remove in final template
- [ ] `<meta name="generator">` (WordPress + WPML) — remove in final template

---

## Pages — Cleanup Status

| Page | Source Reviewed | Copied to html-templates | CSS Localized | Fonts Localized | SVGs Localized | Scripts Stripped | Clean Version | Working Version | Notes |
|------|:--------------:|:------------------------:|:-------------:|:---------------:|:--------------:|:----------------:|:-------------:|:---------------:|-------|
| home | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | GF form replacement pending |
| services | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | |
| services-primary-care | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | |
| locations | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | |
| location-truecare-carlsbad | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | |
| resources | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | |
| about | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | |
| schedule-an-appointment | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | |
| services | ⬜ | ⬜ | ⬜ | ⬜ | |
| services-primary-care | ⬜ | ⬜ | ⬜ | ⬜ | |
| locations | ⬜ | ⬜ | ⬜ | ⬜ | |
| location-truecare-carlsbad | ⬜ | ⬜ | ⬜ | ⬜ | |
| resources | ⬜ | ⬜ | ⬜ | ⬜ | |
| about | ⬜ | ⬜ | ⬜ | ⬜ | |
| schedule-an-appointment | ⬜ | ⬜ | ⬜ | ⬜ | |

---

## Decisions Log

| Date | Decision | Reason |
|------|----------|--------|
| 2026-05-24 | Keep all external image URLs intact during prototype phase | Images still resolve from live truecare.org site; swap locally only when directed |
| 2026-05-24 | Do not remove any markup without discussion | Preserve source fidelity; remove only after explicit agreement |
| 2026-05-24 | Start with home page | User directive |
| 2026-05-24 | Strip GTM, Cookiebot, Blackbaud, Five9, WPML JS, Gravity Forms JS, reCAPTCHA scripts | No visual value in prototype; reduce noise and load time |
| 2026-05-24 | Replace Gravity Forms form with plain HTML form | Prototype needs a functional-looking form without WP dependency |
| 2026-05-24 | Download all CSS files locally to `html-templates/home/assets/css/` | Remove dependency on live truecare.org server for stylesheets |
| 2026-05-24 | Keep WPML language switcher HTML markup | It is part of the visual layout |
| 2026-05-24 | Download fonts locally (`assets/fonts/`) and patch relative paths in child theme CSS | `truecare-theme.css` used `../truecare/fonts/` — correct on WP server, broken locally |
| 2026-05-24 | Patch Divi icon font paths in `divi-core.min.css` to absolute URLs | `url(core/admin/fonts/...)` relative paths resolved nowhere outside the WP server |
| 2026-05-24 | Download SVG icons to `assets/images/` and patch `/wp-content/uploads/` paths in CSS | Root-relative SVG background-image paths rendered as broken blobs locally |
| 2026-05-24 | Keep clean `index.html` frozen; all further modifications go in `index.working.html` | Preserves a verified-correct reference point for each page |
| 2026-05-24 | Add `home-overrides.css` loaded only by `index.working.html` | Scopes working-phase CSS changes so they cannot affect the clean reference file |
