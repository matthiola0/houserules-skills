# Commit message style — EXAMPLE (TypeScript / React web app)

> A filled-in example with Conventional Commits on.

## Hard rules (never violate)
- Never add `Co-Authored-By` or any AI / Claude / Codex attribution or tool signature.
- No emojis, no ad lines (e.g. "Generated with ...").

## Format
- Conventional Commits prefix: on. Subject: `<type>(<optional scope>): <description>`.
  - Types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`, `style`, `perf`.
  - Scope = the area touched (e.g. `auth`, `dashboard`, `api`).
  - Description: imperative, lowercase first letter, no trailing period; subject <= 50 chars.
  - Good: `feat(auth): add refresh-token rotation`, `fix(dashboard): debounce search input`
  - Bad: `added auth`, `feat: Added stuff.`
- Blank line after the subject, then the body (optional). The body explains what / why,
  not a line-by-line restatement of the diff.
- One commit, one thing.

## Example
```
feat(dashboard): cache expensive aggregate query

The summary panel re-ran a 400ms aggregate on every keystroke. Memoize
by filter hash and invalidate on data mutation so typing stays smooth.
```

## Project conventions
- Conventional Commits prefixes: on.
- Reference issues in the body footer when relevant: `Refs #1234`.
