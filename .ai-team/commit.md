# Commit message style — this repo (houserules-skills), live

> The commit rules this repo follows. Its git history is written to this.

## Hard rules (never violate)
- **Never** add `Co-Authored-By` or any AI / Claude / Codex attribution or tool signature.
- No emojis, no ad lines (e.g. "Generated with ...").

## Format
- Subject: imperative, ≤ 50 chars, capitalized first letter, no trailing period.
  - Good: `Add reviewer skill with Codex code-review mode`
  - Bad: `added reviewer`, `update stuff`
- Blank line after the subject, then the body (optional). The body explains what / why,
  not a line-by-line restatement of the diff.
- One commit, one thing.

## Example (from this repo's first commit)
```
Add houserules-skills AI agent team skill pack

Four-role team (CEO/Coder/Reviewer/Tester) as installable Claude Code
skills. CEO orchestrates a brainstorm -> PRD -> SDD -> ... loop; Reviewer
runs on Codex CLI for dual-model review. ...
```

## Project conventions
- Conventional Commits prefixes: off (keep the plain imperative style).
