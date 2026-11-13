# Agent Rules

## Core Principles

### 1. Do Not Change Anything Unless Explicitly Told
- Never modify, refactor, or delete code that the user has not explicitly asked you to change.
- If a task requires changes, only touch the files and sections directly related to the request.
- When in doubt, ask the user for clarification before making any changes.

### 2. Always Ask Questions First
- Before starting any implementation, ask clarifying questions if the task is ambiguous.
- Confirm your understanding of the user's intent before writing code.
- If multiple approaches exist, present options and let the user decide.

### 3. Always Plan Before Implementing
- Create a clear, step-by-step plan before writing any code.
- Share the plan with the user for approval before proceeding.
- Update the plan as new information or requirements emerge.

### 4. Clean Code Architecture
- Write code that is readable, maintainable, and well-structured.
- Follow established project conventions and patterns.
- Prioritize separation of concerns and single responsibility principles.
- Avoid code duplication — extract shared logic into reusable components or utilities.
- Name variables, functions, and components clearly and consistently.

### 5. No Commits or Pushes Without Permission
- Never run `git commit`, `git push`, or any other version control command unless the user explicitly asks you to.
- Do not initiate, stash, or discard changes on your own.
- If the user requests a commit, include clear and descriptive commit messages.

## Project-Specific Conventions

### Astro Components
- All components use the `.astro` file extension.
- Component frontmatter (code fences `---`) contains imports and logic; markup follows after.
- Prefer static rendering; use client-side directives (`client:load`, `client:visible`) only when interactivity is needed.
- Pass props via `Astro.props` destructuring in frontmatter.

### Styling with Tailwind CSS v4
- Use Tailwind utility classes directly in markup.
- Global theme colors are defined as CSS custom properties in `src/styles/global.css` under `@theme`.
- Reference theme colors via Tailwind's `var()` syntax: `text-main-text`, `bg-card`, `border-accent`, etc.
- Neon glow effects use CSS custom properties (`--neon-blue-soft`, `--neon-purple-glow`, etc.).

### TypeScript Interfaces
- Define data shapes in `src/interfaces/` as `.ts` files.
- Use interfaces for component props, data structures, and API responses.
- Import interfaces in component frontmatter for type-safe prop handling.

### i18n Pattern
- Translation data lives in `src/data/[lang]/` as JSON files.
- Pages use `[lang].astro` dynamic routing for language selection.
- Pass translations as props from pages down through sections to components.
- Never hardcode user-facing text in components; always use translation keys.

### How to Follow These Rules
1. **Read** the user's request carefully.
2. **Ask** questions if anything is unclear.
3. **Plan** the implementation steps.
4. **Confirm** the plan with the user.
5. **Implement** only what was agreed upon.
6. **Review** your changes before submitting.
