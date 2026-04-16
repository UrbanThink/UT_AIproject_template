---
applyTo: "src/frontend/**/*,src/ui/**/*,src/components/**/*,src/pages/**/*,src/views/**/*,src/screens/**/*,src/app/**/*,web/**/*,client/**/*,frontend/**/*,**/*.tsx,**/*.jsx,**/*.css,**/*.scss"
---

# Frontend Instructions

Apply these instructions when working on UI code, components, pages, styles, client-side logic, or frontend state management.

## Primary goal

Produce frontend code that is:

- clear
- consistent
- accessible
- predictable
- maintainable
- easy to test

## Component design

- Follow the existing component structure and naming conventions.
- Keep components focused on one responsibility.
- Prefer composition over large monolithic components.
- Extract reusable UI patterns only when repetition is real and stable.
- Keep presentational concerns separate from heavy business logic when possible.

## State management

- Keep state as local as possible.
- Do not introduce global state without a clear reason.
- Be explicit about derived state, async state, loading state, empty state, and error state.
- Avoid duplicating the same source of truth in multiple places.
- Prefer predictable data flow over clever shortcuts.

## UX behavior

- Handle loading, empty, success, and error states explicitly.
- Do not leave the UI in ambiguous or partially broken states.
- Preserve existing user flows unless the task explicitly changes them.
- Avoid surprising behavior, hidden side effects, or abrupt UI changes without feedback.

## Accessibility

- Use semantic elements where possible.
- Preserve keyboard accessibility.
- Ensure interactive elements have clear labels or accessible names.
- Do not rely only on color to convey meaning.
- Be careful when introducing custom controls that weaken accessibility.

## Styling

- Reuse the existing design system, tokens, utility conventions, or component variants before creating new styling patterns.
- Avoid one-off styling if an established pattern already exists nearby.
- Keep styling readable and maintainable.
- Do not introduce visual inconsistency without explicit intent.

## Performance

- Avoid unnecessary rerenders, large inline objects, or unstable callbacks when they matter.
- Be careful with expensive computations in render paths.
- Do not fetch or recompute more than necessary.
- Preserve responsive and smooth interactions.

## Forms and validation

- Validate input clearly.
- Surface validation messages in a user-understandable way.
- Keep form state predictable.
- Do not silently discard user input or reset data unexpectedly.

## Frontend security

- Treat all external data as untrusted.
- Be careful with HTML injection, URL construction, storage of sensitive data, and client-side auth assumptions.
- Do not expose secrets in frontend code.
- Avoid dangerous rendering patterns unless they are strictly necessary and well controlled.

## Tests

When frontend behavior changes:

- add or update relevant component, interaction, or end-to-end tests
- cover expected UI states
- verify user-visible behavior
- avoid brittle selector coupling when possible
- prefer test scenarios that reflect real usage

## What to avoid

- giant components with many responsibilities
- duplicated state
- hidden side effects in rendering
- inaccessible custom controls
- styling drift
- UI logic that is hard to reason about

## Done criteria for frontend work

Frontend work is not complete unless:

- user-visible states are handled
- accessibility is preserved or improved
- state behavior is understandable
- styling is consistent with the surrounding app
- tests are updated when behavior changes