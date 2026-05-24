# Project Reference Notes

Running log of observations, decisions, and things to revisit as we build templates.

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

| Page | Source Reviewed | Copied to html-templates | CSS Extracted | Images Localized | Notes |
|------|:--------------:|:------------------------:|:-------------:|:----------------:|-------|
| home | ✅ | ⬜ | ⬜ | ⬜ | In progress |
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

---

## Questions / Things to Discuss

- [ ] Which scripts should we strip for the first html-templates copy? (GTM, Cookiebot, Five9, Blackbaud, WPML)
- [ ] Should the Gravity Forms contact form be replaced with a simple HTML form in the template?
- [ ] Should we keep the Divi CSS loading from truecare.org CDN, or do we want to download and host it locally?
- [ ] Language switcher (WPML) — include or remove in templates?
