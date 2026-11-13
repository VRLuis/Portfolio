# Portfolio

A personal portfolio website for **Luis Villar Roldán**, a Fullstack Developer. Built with **Astro.js** and styled with a custom **neon-themed dark UI**, the site showcases professional experience, projects, education, and skills — all fully localized in **English** and **Spanish**.

## Tech Stack

| Technology | Version | Purpose |
|---|---|---|
| [Astro](https://astro.build) | 7.x | Static site generator with file-based routing |
| [Tailwind CSS](https://tailwindcss.com) | 4.x | Utility-first styling via Vite plugin |
| TypeScript | — | Type-safe interfaces and component props |
| Node.js | ≥ 22.12.0 | Runtime requirement |

## Project Context

This portfolio is a **static site** — all content is resolved at build time from JSON data files. There's no backend, no database, and no client-side framework. Astro handles routing, rendering, and optimization, producing a fast, accessible site with zero JavaScript by default.

The neon dark theme (inspired by GitHub's dark palette with blue/purple glow accents) is applied through CSS custom properties mapped to Tailwind utilities, creating a consistent visual language across all sections.

## Architecture

The project follows the **Atomic Design** methodology to keep components organized and reusable:

```
src/
├── components/
│   ├── atoms/          # Basic UI elements (SectionHeader, etc.)
│   ├── molecules/      # Simple combinations (ExperienceCard, etc.)
│   ├── organisms/      # Complex compositions (ExperienceList, etc.)
│   └── sections/       # Page section blocks (Experience, Projects, etc.)
├── layouts/            # Page wrappers (Layout.astro with header/footer)
├── pages/              # Astro pages (index.astro, [lang].astro)
├── interfaces/         # TypeScript interfaces for data shapes
├── data/               # i18n content layer (see below)
├── styles/             # Global CSS (neon theme + Tailwind config)
└── assets/             # Static assets (images, logos)
```

### Component Flow

```
Pages → Layouts → Sections → Organisms → Molecules → Atoms
```

Each component is a single `.astro` file. Props flow top-down from pages through sections to the smallest atoms. TypeScript interfaces in `src/interfaces/` define the shape of all data passed between layers.

## Internationalization

Content is fully separated from presentation through a **file-based i18n system**:

- **UI strings** (navigation, buttons, labels) live in `src/data/i18n/[lang].json`.
- **Domain content** (experience, projects, certificates) lives in `src/data/[lang]/[domain].json`.
- Pages use Astro's dynamic routing (`[lang].astro`) to load the correct language files at build time.

### Supported Languages

| Code | Language |
|---|---|
| `en` | English (default) |
| `es` | Spanish |

To add a new language, create a new folder under `src/data/` with translated JSON files mirroring the existing structure, plus a UI strings file in `src/data/i18n/`.

## Styling

The neon dark theme is defined entirely in `src/styles/global.css`:

- **Core colors** use GitHub-inspired dark palette (`#0d1117` background, `#c9d1d9` text, `#58a6ff` accent).
- **Neon glow effects** are layered `box-shadow` and gradient values in CSS custom properties.
- **Grid background** uses a `::after` pseudo-element with `mix-blend-mode: screen` for a subtle glow grid.
- All theme colors are mapped to Tailwind utilities via the `@theme` directive (e.g., `bg-primary`, `text-accent`, `border-card`).

## Getting Started

### Prerequisites

- Node.js ≥ 22.12.0
- [pnpm](https://pnpm.io) (recommended) or npm

### Installation

```bash
pnpm install
```

### Development

```bash
pnpm dev        # Start local dev server with hot reload
pnpm build      # Build for production
pnpm preview    # Preview the production build locally
```

## Design Principles

- **One component, one file** — no splitting components across multiple files.
- **One responsibility per component** — if it does too much, break it down.
- **No hardcoded text** — all user-facing strings come from i18n data files.
- **Static first** — client-side interactivity is used sparingly via Astro's `client:*` directives.
- **400-line limit** — components should stay concise; complex logic belongs in smaller composed pieces.

## Skills

Development guidelines and conventions are documented in the [`skills/`](./skills/) directory:

| File | What it covers |
|---|---|
| [ARCHITECTURE.md](./skills/ARCHITECTURE.md) | Atomic Design structure and Astro conventions |
| [RULES.md](./skills/RULES.md) | Development rules and project-specific conventions |
| [STYLES.md](./skills/STYLES.md) | Tailwind setup, CSS custom properties, and theme system |
| [I18N.md](./skills/I18N.md) | Internationalization data flow and patterns |
| [IMPLEMENTATIONS.md](./skills/IMPLEMENTATIONS.md) | Incremental implementation guidelines |