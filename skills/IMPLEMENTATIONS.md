# Implementation Guidelines

## Small, Focused Implementations

### The 400-Line Rule
- **Never write more than 400 lines of code in a single implementation.**
- If a feature requires more than 400 lines, break it into smaller, logical chunks.
- Each chunk should be reviewable on its own and build upon the previous one.

### Why Small Implementations?
- **Easier to review**: Smaller changes are faster to read and understand.
- **Fewer bugs**: Less code means fewer places for errors to hide.
- **Simpler debugging**: When something breaks, the scope of investigation is smaller.
- **Better focus**: Working on one small thing at a time leads to higher quality code.

### How to Apply This Rule

#### 1. Break Features into Steps
Before implementing a feature, divide it into small, independent steps:
- Step 1: Create the basic structure and types
- Step 2: Implement the core logic
- Step 3: Add the UI components
- Step 4: Connect everything and handle edge cases

#### 2. One Component at a Time
- Build one component per implementation session.
- Do not create multiple components in a single change unless they are very small.
- Test each component before moving to the next.

#### 3. Bilingual Content Requirement
- **Every implementation that introduces new content must provide both an English (`en`) and Spanish (`es`) version.**
- When creating or updating data files in `src/data/`, always add the corresponding entries in both `src/data/en/` and `src/data/es/`.
- When adding new UI strings (labels, buttons, headings), update both `src/data/i18n/en.json` and `src/data/i18n/es.json`.
- Do not ship an implementation with placeholder or missing translations — both languages must be complete before the step is considered done.
- If a translation is uncertain, use a clear placeholder (e.g., `"TODO_es"`) and flag it for review rather than leaving the key missing.

#### 4. Incremental Progress
- Commit or present each small implementation before starting the next.
- Each step should leave the codebase in a working state.
- Never leave the project in a broken or incomplete state.

#### 5. Review Before Continuing
- After each implementation, review the code for:
  - Correctness: Does it work as intended?
  - Cleanliness: Is the code well-structured and readable?
  - Completeness: Are edge cases handled?
- Only proceed to the next step after the current one is solid.

### What Counts as "Lines"?
- The 400-line limit refers to **new or modified lines** in a single implementation.
- Comments, blank lines, and imports count toward the total.
- If you are close to the limit, stop and review — do not push through.

### When to Stop and Ask
- If you realize a task will exceed 400 lines, **stop and inform the user**.
- Propose a breakdown of the task into smaller steps.
- Get approval before continuing with the next step.

## Summary
1. Plan small — break tasks into chunks under 400 lines.
2. Implement one chunk at a time.
3. Include both English and Spanish translations for every piece of content.
4. Review each chunk before proceeding.
5. Communicate if a task is larger than expected.
