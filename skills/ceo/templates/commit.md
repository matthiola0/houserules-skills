# Commit message style (house rules)

> The Coder follows this on every commit. Defaults to a clean, no-AI-attribution style
> that matches most people's habits.
> A complete filled example: `examples/typescript-web/.ai-team/commit.md`.

## Hard rules (never violate)
- **Never** add `Co-Authored-By` or any AI / Claude / Codex attribution or tool signature.
- No emojis, no ad lines (e.g. "Generated with ...").

## Format
- **Conventional Commits prefix: on (default).** Subject form:
  `<type>(<optional scope>): <description>`
  - Types: `feat` (feature), `fix` (bug), `docs`, `refactor`, `test`, `chore`,
    `style` (formatting only), `perf`. Breaking change: add `!` (`feat!:`) or a
    `BREAKING CHANGE:` body footer.
  - Description: **imperative**, lowercase first letter, no trailing period.
  - Whole subject ≤ 50 chars where practical.
  - Good: `feat: add retry to upload client`, `fix(auth): handle expired token`
  - Bad: `added retry`, `feat: Added retry.`, `fixes stuff`
- Blank line after the subject, then the body (optional). The body explains **what / why**,
  not a line-by-line restatement of the diff.
- One commit, one thing; don't mix unrelated changes.

## Example
```
feat: add retry with backoff to upload client

Uploads failed intermittently on flaky networks. Retry up to 3 times
with exponential backoff so transient 5xx no longer surface to users.
```

## Toggle
- To turn the prefix off and use plain imperative subjects (e.g. `Add retry to upload
  client`), set Conventional Commits prefixes: off here.
