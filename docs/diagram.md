# Folder Structure Diagram

```
tc-pillarpage-templates/
├── README.md
├── docs/
│   ├── diagram.md                                    # This file — annotated folder tree
│   └── reference.md                                  # Running log: decisions, brand tokens, methodology, status
│
├── cloned-pages/                                     # Raw HTTrack output — reference only, do not edit
│   ├── home/
│   │   └── index.html
│   ├── services/
│   │   └── index.html
│   ├── services-primary-care/
│   │   └── index.html
│   ├── locations/
│   │   └── index.html
│   ├── location-truecare-carlsbad/
│   │   └── index.html
│   ├── resources/
│   │   └── index.html
│   ├── about/
│   │   └── index.html
│   └── schedule-an-appointment/
│       └── index.html
│
├── html-templates/                                   # Cleaned, standalone HTML/CSS templates
│   ├── home/                                         # ✅ COMPLETE — clean + working versions done
│   │   ├── index.original.html                       # 🔒 Locked backup — identical to cloned source, never edit
│   │   ├── index.html                                # ✅ Clean reference — scripts stripped, CSS/fonts/SVGs localized, never edit
│   │   ├── index.working.html                        # 🔄 Active working file — GF replaced, all brand colors swapped
│   │   └── assets/
│   │       ├── css/
│   │       │   ├── divi-core.min.css                 # Divi theme core — icon font paths patched to absolute URLs
│   │       │   ├── truecare-theme.css                # Child theme — font + SVG paths patched; original colors (linked by index.html only)
│   │       │   ├── truecare-theme-working.css        # Child theme — working copy; all brand colors swapped (linked by index.working.html)
│   │       │   ├── home-overrides.css                # 🖊 Scoped overrides for index.working.html only (last CSS link)
│   │       │   ├── monarch-social.css
│   │       │   ├── divi-machine-ajax-filter.min.css
│   │       │   ├── divi-machine.min.css
│   │       │   ├── divi-machine-carousel.min.css
│   │       │   ├── dwd-map-extended.min.css
│   │       │   ├── instagram-feed.min.css
│   │       │   ├── team-showcase.min.css
│   │       │   ├── wpml-switcher.min.css
│   │       │   ├── algolia-autocomplete.css
│   │       │   ├── mediaelement.min.css
│   │       │   ├── wp-mediaelement.min.css
│   │       │   ├── gravityforms-basic.min.css
│   │       │   ├── gravityforms-theme-components.min.css  # 0 bytes — GF being replaced, not critical
│   │       │   └── gravityforms-theme.min.css
│   │       ├── fonts/                                # Downloaded from truecare.org — served locally
│   │       │   ├── Forma-Regular.woff2
│   │       │   ├── Forma-Medium.woff2
│   │       │   ├── Forma-Bold.woff2
│   │       │   ├── mulish-v12-latin-regular.woff2
│   │       │   ├── mulish-v12-latin-500.woff2
│   │       │   ├── mulish-v12-latin-600.woff2
│   │       │   └── mulish-v12-latin-700.woff2
│   │       ├── images/                               # SVG icons downloaded from WP uploads — served locally
│   │       │   ├── white-chevron-links-9x16-1.svg
│   │       │   ├── pink-chevron-links-9x16-1.svg
│   │       │   ├── yellow-chevron-links-9x16-1.svg
│   │       │   ├── file-download-15x19-2.svg
│   │       │   ├── play-button-pink-22x22-1.svg
│   │       │   └── calendar-17x19-1.svg
│   │       └── js/                                   # (empty — no local JS needed yet)
│   ├── services/
│   │   └── (not started)
│   ├── services-primary-care/
│   │   └── (not started)
│   ├── locations/
│   │   └── (not started)
│   ├── location-truecare-carlsbad/
│   │   └── (not started)
│   ├── resources/
│   │   └── (not started)
│   ├── about/
│   │   └── (not started)
│   └── schedule-an-appointment/
│       └── (not started)
│
└── elementor-templates/                              # Elementor JSON exports, ready to import (future phase)
    ├── home/
    │   └── home.json
    ├── services/
    │   └── services.json
    ├── services-primary-care/
    │   └── services-primary-care.json
    ├── locations/
    │   └── locations.json
    ├── location-truecare-carlsbad/
    │   └── location-truecare-carlsbad.json
    ├── resources/
    │   └── resources.json
    ├── about/
    │   └── about.json
    └── schedule-an-appointment/
        └── schedule-an-appointment.json
```

---

## File Role Legend

| Emoji | Meaning |
|-------|---------|
| 🔒 | Locked — never edit under any circumstances |
| ✅ | Frozen clean reference — do not modify |
| 🔄 | Active working file — all modifications go here |
| 🖊 | Scoped override file — only affects the working copy |

---

## Three-File Pattern (per page)

Every page in `html-templates/` follows this pattern:

```
index.original.html   ← exact copy of cloned source (locked)
index.html            ← clean reference (scripts stripped, assets localized, frozen)
index.working.html    ← active modifications (colors, forms, content)
```

The clean `index.html` and `index.working.html` each link their own CSS:
- `index.html`         → `assets/css/truecare-theme.css`         (original colors)
- `index.working.html` → `assets/css/truecare-theme-working.css` (brand colors swapped)
- `index.working.html` also appends `assets/css/<page>-overrides.css` as last link

---

## Preview Servers (Codespaces)

| Port | File served | URL |
|------|------------|-----|
| 8080 | `cloned-pages/home/index.html` | `https://probable-bassoon-x566699qg52gxv-8080.app.github.dev/` |
| 8081 | `html-templates/home/` | `https://probable-bassoon-x566699qg52gxv-8081.app.github.dev/index.working.html` |

> **Note:** Port 8081 defaults to `index.html` — always append `/index.working.html` explicitly to reach the working file.

---

> All folder and file names use **kebab-case**.
> Empty folders are tracked by git via `.gitkeep` files (removed once real files are added).
