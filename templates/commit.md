# Commit message style (house rules)

> The Coder follows this on every commit. Defaults to a clean, no-AI-attribution style
> that matches most people's habits.

## Hard rules (never violate)
- **Never** add `Co-Authored-By` or any AI / Claude / Codex attribution or tool signature.
- No emojis, no ad lines (e.g. "Generated with ...").

## Format
- Subject: **imperative**, ≤ 50 chars, capitalized first letter, no trailing period.
  - Good: `Add retry to upload client`
  - Bad: `added retry`, `fixes stuff`
- Blank line after the subject, then the body (optional). The body explains **what / why**,
  not a line-by-line restatement of the diff.
- One commit, one thing; don't mix unrelated changes.

## Example
```
Add retry with backoff to upload client

Uploads failed intermittently on flaky networks. Retry up to 3 times
with exponential backoff so transient 5xx no longer surface to users.
```

## Optional conventions (can enable at init)
- Conventional Commits prefixes (`feat:` / `fix:` / `refactor:` ...): <on/off>
