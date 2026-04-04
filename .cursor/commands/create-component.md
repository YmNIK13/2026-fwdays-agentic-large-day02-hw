# Create Component

## Overview

Create a new component that fits the existing codebase instead of generating a generic standalone example. Match the surrounding architecture, naming, styling, and testing patterns.

## Steps

1. **Inspect Local Context**
   - Find the target folder and read nearby components first
   - Reuse the established file structure, styling approach, and export pattern
   - Check `.cursor/rules` for package-specific constraints before writing code
2. **Design the Component API**
   - Define the smallest useful prop surface
   - Use a typed props shape such as `{ComponentName}Props`
   - Prefer named exports and functional components with hooks
   - Avoid `any`, `@ts-ignore`, and default exports unless the local code already requires them
3. **Implement the Component**
   - Keep component and file naming consistent with the surrounding code
   - Use `import type` for type-only imports
   - Extract small helpers only when they clarify logic or remove duplication
   - Add brief comments only when the code would otherwise be hard to parse
4. **Integrate Cleanly**
   - Wire exports, imports, and any required usage points
   - Preserve the existing design system or visual language
   - Do not introduce new dependencies without explicit approval
5. **Verify**
   - Add or update colocated tests when the component has meaningful behavior
   - Check loading, empty, error, and interaction states when applicable
   - Run relevant checks if the task requires verification

## Output Requirements

- Create production-ready code, not a sketch
- Keep the implementation scoped to the requested component
- Explain any assumptions when requirements are ambiguous
- If blocked by missing design or API details, ask only the minimum necessary questions

## Create Component Checklist

- [ ] Inspected nearby components and reused local patterns
- [ ] Defined a minimal typed props API
- [ ] Used a functional component and named export
- [ ] Avoided `any`, `@ts-ignore`, and unnecessary complexity
- [ ] Kept naming, styling, and file placement consistent
- [ ] Integrated exports/imports cleanly
- [ ] Added or updated tests when behavior warranted it
- [ ] Covered key states and interactions where applicable
