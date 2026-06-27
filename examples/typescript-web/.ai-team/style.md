# Code style — EXAMPLE (TypeScript / React web app)

> A filled-in example. Every `<...>` from the template is replaced with a real value.

## General
- Prefer the conventions already used in the file / project; apply these defaults only
  when they don't conflict with what's there.
- Clear > clever. Name things in plain words; avoid pointless abbreviations.
- No dead code, no commented-out code.

## Language / framework
- Primary language: TypeScript (strict mode), React 18, Vite
- Formatter: Prettier (its output is the source of truth; never hand-format around it)
- Linter: ESLint (typescript-eslint, react-hooks); no warnings on commit

## Naming
- Variables/functions: camelCase
- Types/interfaces/components: PascalCase
- Constants: UPPER_SNAKE
- Filenames: kebab-case for modules, PascalCase for component files (`UserCard.tsx`)

## Formatting
- Indent: 2 spaces
- Line width: 100
- Quotes: single; semicolons: yes

## Tests
- Framework: Vitest + React Testing Library
- Require tests with new features: yes (at least the happy path + one edge case)

## Error handling
- Validate external input at the boundary (zod schemas for API responses).
- Never swallow errors silently; surface them to an error boundary or toast.
- No `any`; use `unknown` + narrowing when a type is genuinely dynamic.

## Comments (in code)
- Explain why, not what; match the density of surrounding code.
- Comment language: English.
- When to comment: non-obvious intent, invariants, workarounds (link the issue/PR).
- Doc-comments for exported functions/types: JSDoc (`/** ... */`) with a one-line summary.
- TODO/FIXME format: `// TODO(alex): switch to the v2 endpoint once shipped`

## Documentation & prose (README, docs, commit bodies)
- Prose language: English.
- Voice / tone: concise, direct, second person; no marketing fluff.
- Structure: lead with the why, short sections, tables for structured info, one idea per
  sentence.
- Formatting: code / paths / commands in `backticks`; copy-pasteable fenced blocks for
  examples; headings in sentence case.
- Keep docs in sync with behavior — update them in the same PR that changes behavior.
