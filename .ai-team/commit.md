# Commit message style — this repo (houserules-skills), live

> The commit rules this repo follows. Its git history is written to this.

## Hard rules (never violate)
- **Never** add `Co-Authored-By` or any AI / Claude / Codex attribution or tool signature.
- No emojis, no ad lines (e.g. "Generated with ...").

## Format
- **Conventional Commits prefix: on.** Subject: `<type>(<optional scope>): <description>`.
  - Types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`, `style`, `perf`.
  - Description: imperative, lowercase first letter, no trailing period; subject ≤ 50 chars.
  - Good: `docs: translate all content to English`, `feat: add reviewer code-review mode`
  - Bad: `added reviewer`, `update stuff`
- Blank line after the subject, then the body (optional). The body explains what / why,
  not a line-by-line restatement of the diff.
- One commit, one thing.

## Example
```
feat: add houserules-skills AI agent team skill pack

Four-role team (CEO/Coder/Reviewer/Tester) as installable Claude Code
skills. CEO orchestrates a brainstorm -> PRD -> SDD -> ... loop; Reviewer
runs on Codex CLI for dual-model review. ...
```

## Project conventions
- Conventional Commits prefixes: on.
- Note: commits before `docs: enable Conventional Commits prefix by default` predate this
  switch and use plain imperative subjects.
