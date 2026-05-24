# Folder Structure Diagram

```
tc-pillarpage-templates/
├── README.md
├── docs/
│   └── diagram.md                                    # This file
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
│   ├── home/
│   │   ├── index.original.html                       # 🔒 Locked backup — do not edit
│   │   ├── index.html                                # ✅ Clean reference — do not edit
│   │   ├── index.working.html                        # 🔄 Active working file — modifications go here
│   │   └── assets/
│   │       ├── css/
│   │       │   ├── divi-core.min.css                 # Divi theme core (icon font paths → absolute URLs)
│   │       │   ├── truecare-theme.css                # Child theme (font + SVG paths → local)
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
│   │       │   ├── gravityforms-theme-components.min.css  # 0 bytes — GF being replaced
│   │       │   ├── gravityforms-theme.min.css
│   │       │   └── home-overrides.css                # 🖊 Scoped overrides for index.working.html only
│   │       ├── fonts/
│   │       │   ├── Forma-Regular.woff2
│   │       │   ├── Forma-Medium.woff2
│   │       │   ├── Forma-Bold.woff2
│   │       │   ├── mulish-v12-latin-regular.woff2
│   │       │   ├── mulish-v12-latin-500.woff2
│   │       │   ├── mulish-v12-latin-600.woff2
│   │       │   └── mulish-v12-latin-700.woff2
│   │       ├── images/
│   │       │   ├── white-chevron-links-9x16-1.svg
│   │       │   ├── pink-chevron-links-9x16-1.svg
│   │       │   ├── yellow-chevron-links-9x16-1.svg
│   │       │   ├── file-download-15x19-2.svg
│   │       │   ├── play-button-pink-22x22-1.svg
│   │       │   └── calendar-17x19-1.svg
│   │       └── js/
│   ├── services/
│   │   ├── index.html
│   │   └── assets/ { css/, js/, images/ }
│   ├── services-primary-care/
│   │   ├── index.html
│   │   └── assets/ { css/, js/, images/ }
│   ├── locations/
│   │   ├── index.html
│   │   └── assets/ { css/, js/, images/ }
│   ├── location-truecare-carlsbad/
│   │   ├── index.html
│   │   └── assets/ { css/, js/, images/ }
│   ├── resources/
│   │   ├── index.html
│   │   └── assets/ { css/, js/, images/ }
│   ├── about/
│   │   ├── index.html
│   │   └── assets/ { css/, js/, images/ }
│   └── schedule-an-appointment/
│       ├── index.html
│       └── assets/ { css/, js/, images/ }
│
└── elementor-templates/                              # Elementor JSON exports, ready to import
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

> All folder and file names use **kebab-case**.
> Empty folders are tracked by git via `.gitkeep` files (removed once real files are added).
