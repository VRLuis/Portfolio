# Styling Guidelines

## Technology Stack

- **Tailwind CSS v4** via `@tailwindcss/vite` plugin
- Configured in `astro.config.mjs` under Vite plugins
- Global styles in `src/styles/global.css`

## Theme System

### CSS Custom Properties

All theme colors are defined as CSS custom properties in `src/styles/global.css` under `:root`. Tailwind references them via the `@theme` directive.

#### Core Colors
```css
--primary-color: #0d1117;          /* Dark background */
--card-color: #161b22c3;           /* Semi-transparent card background */
--main-text-color: #c9d1d9;        /* Primary text */
--secondary-text-color: #8b949e;   /* Muted text */
--accent-color: #58a6ff;           /* Primary accent (blue) */
--secondary-accent-color: #366ece; /* Darker accent */
--tertiary-accent-color: #1d2e4d;  /* Subtle accent */
--danger-color: #872d2d;           /* Error/danger state */
--secondary-danger-color: #531b1b; /* Darker danger */
```

#### Neon Glow Effects
```css
--neon-blue-soft: rgba(88, 166, 255, 0.18);
--neon-blue-medium: rgba(88, 166, 255, 0.25);
--neon-blue-strong: rgba(88, 166, 255, 0.35);
--neon-purple-soft: rgba(248, 100, 255, 0.1);
--neon-purple-medium: rgba(248, 100, 255, 0.24);
--neon-purple-glow: rgba(255, 82, 222, 0.18);
```

#### Neon Grid Background
```css
--neon-blur: 5rem;
--neon-grid-size: 16rem;
```

#### Profile Shadows
```css
--profile-shadow-soft: 0 20px 40px var(--neon-blue-medium), 0 0 60px var(--neon-purple-soft);
--profile-shadow-strong: 0 30px 60px var(--neon-blue-strong), 0 0 90px var(--neon-purple-glow);
```

### Tailwind Theme Mapping

The `@theme` directive maps CSS custom properties to Tailwind utility classes:

| CSS Variable | Tailwind Class |
|---|---|
| `--primary-color` | `bg-primary`, `text-primary` |
| `--card-color` | `bg-card`, `text-card` |
| `--main-text-color` | `text-main-text` |
| `--secondary-text-color` | `text-secondary-text` |
| `--accent-color` | `text-accent`, `border-accent`, `bg-accent` |
| `--secondary-accent-color` | `text-secondary-accent`, `bg-secondary-accent` |
| `--tertiary-accent-color` | `bg-tertiary-accent` |
| `--danger-color` | `text-danger`, `bg-danger` |
| `--secondary-danger-color` | `bg-secondary-danger` |

## Styling Conventions

### Utility-First Approach
- Use Tailwind utility classes directly in component markup.
- Avoid custom CSS in Astro components unless necessary for animations or complex effects.
- Prefer composition of utilities over arbitrary values.

### When to Use Custom CSS
- Complex animations or keyframes not covered by Tailwind.
- Pseudo-element effects requiring specific positioning.
- Neon glow effects that need layered `box-shadow` or `background-image` with gradients.

### Scrollbar Styling
- Custom thin scrollbar is defined globally in `global.css`.
- Uses accent color for thumb, primary color for track.
- Do not override scrollbar styles in components.

### Background Effects
- The body background uses a neon grid pattern via `body::after` pseudo-element.
- Grid lines use `mix-blend-mode: screen` for the glow effect.
- Do not add competing background effects to full-width sections.

### Responsive Design
- Use Tailwind's responsive prefixes: `md:`, `lg:`, `xl:`.
- The breakpoint `md:` is the most commonly used (tablet and up).
- Test layouts at both mobile and desktop widths.

## File Organization
- All global styles live in `src/styles/global.css`.
- Component-specific styles go inline in the `.astro` file using Tailwind classes.
- Do not create additional global CSS files unless a new, distinct style domain is needed.
