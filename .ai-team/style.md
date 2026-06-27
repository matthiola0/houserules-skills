# Style — this repo (houserules-skills), live

> This repo's content is Markdown (SKILL.md, docs, templates), so "code style" here means
> **writing style**.

## Writing principles
- Clear > fancy. One sentence, one idea; cut words you can cut (echoing ceo-brain's
  "delete first").
- English throughout. Keep technical terms / commands / filenames as-is.
- Always mark commands, paths, and filenames with backticks (e.g. `.ai-team/commit.md`,
  `codex review`).

## SKILL.md conventions
- Frontmatter must include `name` (lowercase-hyphen, matching the folder) and `description`.
- Write `description` to clearly say "when to use this skill" — that's how it gets
  auto-selected.
- Use numbered sections (§) + explicit steps in the body, so a dispatched role can follow
  without guessing.

## Doc conventions
- Use tables for structured "role / file / responsibility" type information.
- Always give copy-pasteable fenced code blocks for examples.
- Cross-reference with relative links (e.g. `[customization.md](docs/customization.md)`).

## Consistency
- Role names are fixed: CEO / Coder / Reviewer / Tester (non-code: Drafter / Editor /
  Fact-checker).
- Artifact names are fixed: `prd.md` / `sdd.md` (or `outline.md`) / `plan.md` / `reviews/` /
  `tests/`.
