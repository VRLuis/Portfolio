# Architecture Guidelines

## Project Overview

This is an **Astro.js** static portfolio site with internationalization (i18n) support, styled with **Tailwind CSS v4** and a custom neon theme.

## Atomic Design Structure

We follow the **Atomic Design** methodology to organize components and keep the codebase clean, predictable, and easy to navigate.

### Component Hierarchy

1. **Atoms** — The smallest, most basic building blocks. Cannot be broken down further.
   - Examples: `SectionHeader.astro`, buttons, icons, typography elements
   - Location: `src/components/atoms/`

2. **Molecules** — Combinations of atoms that form simple, functional units.
   - Examples: `ExperienceCard.astro` (combines company info, dates, technologies)
   - Location: `src/components/molecules/`

3. **Organisms** — Complex UI components made of molecules and/or atoms.
   - Examples: `ExperienceList.astro`, `FormationList.astro` (list renderers)
   - Location: `src/components/organisms/`

4. **Sections** — Page-level sections that compose organisms into full content blocks.
   - Examples: `Experience.astro`, `Projects.astro`, `About.astro`
   - Location: `src/components/sections/`
   - This layer sits between organisms and pages, representing major page regions.

5. **Layouts** — Wrapper components that provide page structure (header, footer, nav).
   - Example: `Layout.astro`
   - Location: `src/layouts/`

6. **Pages** — Astro page files that connect layouts, sections, and data.
   - Examples: `index.astro`, `[lang].astro` (language-routed pages)
   - Location: `src/pages/`

### Folder Structure
```
src/
├── components/
│   ├── atoms/          # Basic UI elements (SectionHeader, etc.)
│   ├── molecules/      # Simple component combinations (ExperienceCard, etc.)
│   ├── organisms/      # Complex compositions (ExperienceList, FormationList, etc.)
│   └── sections/       # Page section blocks (Experience, Projects, About, etc.)
├── layouts/            # Page wrappers (Layout.astro)
├── pages/              # Astro pages (index.astro, [lang].astro, etc.)
├── interfaces/         # TypeScript interfaces (ExperienceInterface, etc.)
├── data/               # i18n data layer
│   ├── en/             # English translations
│   ├── es/             # Spanish translations
│   └── i18n/           # i18n helper utilities
├── styles/             # Global CSS (global.css with Tailwind + neon theme)
└── assets/             # Static assets (images, logos, etc.)
```

### Rules for Atomic Structure
- **Each component has one responsibility** — if a component does too much, break it down.
- **Each component is a single file** — Astro components (`.astro`) keep markup, logic, and styles in one file. Do not split a component across multiple files.
- **Atoms should not contain other components** — they are pure, standalone elements.
- **Molecules compose atoms** — they should not contain other molecules.
- **Organisms compose molecules and atoms** — they represent distinct UI blocks like lists or grids.
- **Sections compose organisms** — they are major page regions with their own styling and structure.
- **Layouts define page chrome** — header, footer, navigation, and global structure. No business logic.
- **Pages connect everything** — they import layouts, sections, and data to render complete views.
- **Use TypeScript interfaces** — define types in `src/interfaces/` for component props and data shapes.

### Astro-Specific Conventions
- **Fragments**: Astro uses `<Fragment>` or `<>...</>` for wrapping multiple elements.
- **Slots**: Use Astro's slot system for composable components.
- **Client directives**: Use `client:load`, `client:visible`, `client:only` sparingly; prefer static rendering.
- **i18n routing**: Pages use `[lang].astro` dynamic segments for language-based routing.
- **Data loading**: Translation data is loaded from `src/data/[lang]/` JSON files at build time.

### Why This Matters
- **Clarity**: Every developer knows where to find and place components.
- **Reusability**: Atoms and molecules can be reused across multiple organisms and sections.
- **Maintainability**: Changes to small components ripple predictably through the system.
- **Scalability**: New features are added by composing existing building blocks.
- **i18n support**: The data layer separates content from presentation, enabling easy localization.
