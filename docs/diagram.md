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
│   │   ├── index.html
│   │   └── assets/
│   │       ├── css/
│   │       ├── js/
│   │       └── images/
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
