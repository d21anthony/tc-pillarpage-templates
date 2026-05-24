# TC Pillar Page Templates

A collection of landing page templates cloned from reference sites and converted into clean, reusable HTML/CSS files and WordPress Elementor templates for internal use.

---

## Overview

This project takes ~6 real-world landing pages cloned via [HTTrack](https://www.httrack.com/) and converts them into two deliverable formats:

1. **Standalone HTML/CSS templates** — cleaned, self-contained pages that faithfully replicate the original aesthetic.
2. **WordPress Elementor templates** — `.json` files importable via Elementor's template library or site kit.

> **Design principle:** Preserve the visual aesthetic and layout of the cloned source pages exactly. Deviations are made only when explicitly directed.

---

## Pages

| Slug | Description |
|------|-------------|
| `home` | Main landing / homepage |
| `services` | Services overview page |
| `services-primary-care` | Primary care services page |
| `locations` | Locations listing page |
| `location-truecare-carlsbad` | TrueCare Carlsbad location page |
| `resources` | Resources / content hub page |
| `about` | About us page |
| `schedule-an-appointment` | Appointment booking / CTA page |

---

## Progress Tracker

| Page | Cloned | Cleaned | HTML/CSS | Elementor | Tested |
|------|:------:|:-------:|:--------:|:---------:|:------:|
| home | ✅ | ⬜ | ⬜ | ⬜ | ⬜ |
| services | ✅ | ⬜ | ⬜ | ⬜ | ⬜ |
| services-primary-care | ✅ | ⬜ | ⬜ | ⬜ | ⬜ |
| locations | ✅ | ⬜ | ⬜ | ⬜ | ⬜ |
| location-truecare-carlsbad | ✅ | ⬜ | ⬜ | ⬜ | ⬜ |
| resources | ✅ | ⬜ | ⬜ | ⬜ | ⬜ |
| about | ✅ | ⬜ | ⬜ | ⬜ | ⬜ |
| schedule-an-appointment | ✅ | ⬜ | ⬜ | ⬜ | ⬜ |

**Legend:** ✅ Done &nbsp;|&nbsp; 🔄 In Progress &nbsp;|&nbsp; ⬜ Not Started

---

## Folder Structure

See [docs/diagram.md](docs/diagram.md) for the full annotated tree.

```
tc-pillarpage-templates/
├── docs/
├── cloned-pages/
├── html-templates/
└── elementor-templates/
```

All folder and file names use **kebab-case**.

---

## Workflow

Each page follows this conversion pipeline:

```
1. Clone with HTTrack
       ↓
2. Clean up raw HTML/CSS
   (remove HTTrack artifacts, fix paths, strip inline scripts)
       ↓
3. Build standalone HTML/CSS template
   (self-contained, pixel-accurate, no dependencies on the original server)
       ↓
4. Convert to Elementor template (JSON)
   (rebuild layout in Elementor, matching the HTML/CSS template)
       ↓
5. Export via Elementor template library → save as .json
       ↓
6. Test import on WordPress staging site
```

---

## Tech Stack

| Phase | Tools |
|-------|-------|
| Cloning | [HTTrack](https://www.httrack.com/) |
| HTML/CSS editing | HTML5, CSS3 — any code editor |
| WordPress templating | [Elementor](https://elementor.com/) (template JSON export/import) |
| Version control | Git / GitHub |

---

## Getting Started

### Viewing HTML templates locally

Open any `html-templates/<page-name>/index.html` directly in a browser — no build step required.

### Importing an Elementor template

1. In WordPress, go to **Templates → Saved Templates** (or use the Elementor editor).
2. Click **Import Templates** and select the `.json` file from `elementor-templates/<page-name>/`.
3. Apply the template to a new or existing page.

---

## Conventions

- All folders and files: `kebab-case`
- One folder per page in each phase directory (`cloned-pages/`, `html-templates/`, `elementor-templates/`)
- Raw cloned files in `cloned-pages/` are **read-only reference** — never edit them directly
- Document any intentional deviations from the source design in `docs/`
- Update the Progress Tracker above as each stage is completed

---

## Notes

- Source pages were cloned for internal design reference only.
- Elementor export format (single-page `.json` vs. full site kit `.zip`) to be confirmed once Elementor phase begins.
