# Folder Structure Diagram

```
tc-pillarpage-templates/
├── README.md
├── docs/
│   └── diagram.md                                    # This file
├── cloned-pages/                                     # Raw HTTrack output (reference only, do not edit)
│   ├── home/
│   ├── services/
│   ├── services-primary-care/
│   ├── locations/
│   ├── location-truecare-carlsbad/
│   ├── resources/
│   ├── about/
│   └── schedule-an-appointment/
├── html-templates/                                   # Cleaned, standalone HTML/CSS templates
│   ├── home/
│   │   ├── index.html
│   │   └── assets/
│   │       ├── css/
│   │       ├── js/
│   │       └── images/
│   ├── services/
│   │   ├── index.html
│   │   └── assets/ ...
│   ├── services-primary-care/
│   │   ├── index.html
│   │   └── assets/ ...
│   ├── locations/
│   │   ├── index.html
│   │   └── assets/ ...
│   ├── location-truecare-carlsbad/
│   │   ├── index.html
│   │   └── assets/ ...
│   ├── resources/
│   │   ├── index.html
│   │   └── assets/ ...
│   ├── about/
│   │   ├── index.html
│   │   └── assets/ ...
│   └── schedule-an-appointment/
│       ├── index.html
│       └── assets/ ...
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
