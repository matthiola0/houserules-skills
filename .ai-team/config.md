# .ai-team master settings — this repo (houserules-skills)

> This is the repo's own live config (dogfooding): houserules-skills is developed with
> these very rules. It also doubles as a filled-in example for new users — compare it to
> the blank skills/ceo/templates/ to see what a completed config looks like.

## Project
- Name: houserules-skills
- Default task type: writing (this repo's content is Markdown skill files and docs, not
  compiled code)

## Enabled roles
- coder: on (here "code" = skill / doc writing, i.e. the Drafter mode)
- reviewer: on (Editor mode for wording and consistency; technical snippets can use Codex
  design review)
- tester: off (no runnable product here; acceptance is a manual dry-run of the /ceo flow)

## Model split
- CEO: Claude (reads ceo-brain.md)
- Coder/Drafter: Claude
- Reviewer/Editor: Codex CLI or a second tool

## File locations
- Style: .ai-team/style.md
- Commit style: .ai-team/commit.md
- CEO brain: skills/ceo/templates/ceo-brain.md (this repo maintains that default brain itself)
- Review reports: .ai-team/reviews/ (git-ignored)
- Test reports: .ai-team/tests/ (git-ignored)
