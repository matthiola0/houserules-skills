# Code style (house rules)

> The source of truth when the Coder writes and the Reviewer audits. Filled during init
> from your answers; editable any time.
> Top principle: **new code should read like the existing code in the project** — the
> below are defaults for when the existing convention is unclear.

## General
- Prefer the conventions already used in the file / project; apply these defaults only
  when they don't conflict with what's there.
- Clear > clever. Name things in plain words; avoid pointless abbreviations.
- No dead code, no commented-out code.

## Language / framework
- Primary language: <e.g. TypeScript / Python>
- Formatter: <e.g. Prettier / Black / gofmt> — its output is the source of truth
- Linter: <e.g. ESLint / Ruff>

## Naming
- Variables/functions: <e.g. camelCase / snake_case>
- Types/classes: <e.g. PascalCase>
- Constants: <e.g. UPPER_SNAKE>
- Filenames: <e.g. kebab-case>

## Formatting
- Indent: <e.g. 2 spaces>
- Line width: <e.g. 100>
- Quotes: <e.g. single>

## Tests
- Framework: <e.g. Vitest / pytest>
- Require tests with new features: <yes/no>

## Error handling
- <preferences, e.g.: don't swallow exceptions, validate at boundaries, always validate
  external input>

## Comments (in code)
- Default: explain **why**, not restate **what**; match the density of surrounding code.
- Comment language: <e.g. English>
- When to comment: <e.g. only non-obvious intent, invariants, gotchas, workarounds; never
  narrate obvious code>
- Doc-comments for public APIs: <e.g. JSDoc / Google-style docstrings / rustdoc / none>
- TODO/FIXME format: <e.g. `// TODO(owner): ...`>

## Documentation & prose (README, docs, commit bodies)
- Prose language: <e.g. English>
- Voice / tone: <e.g. concise, direct, second person; no marketing fluff>
- Structure: <e.g. lead with the why, short sections, tables for structured info, one idea
  per sentence>
- Formatting: code / paths / commands in `backticks`; copy-pasteable fenced blocks for
  examples; headings in <sentence case / Title Case>
- Keep docs in sync with behavior — update them in the same change that alters behavior.
