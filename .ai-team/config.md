# .ai-team master settings — this repo (houserules-skills)

> This is the repo's own live config (dogfooding): houserules-skills is developed with
> these very rules. It also doubles as a filled-in example for new users — compare it to
> the blank skills/hr-ceo/templates/ to see what a completed config looks like.
>
> Note: in a normal consuming project, init git-ignores the whole .ai-team/. This repo
> deliberately commits its .ai-team/ instead, so the example is visible on GitHub.

## Project
- Name: houserules-skills
- Default task type: writing (this repo's content is Markdown skill files and docs, not
  compiled code)

## Enabled roles
- coder: on (here "code" = skill / doc writing, i.e. the Drafter mode)
- reviewer: on (Editor mode for wording and consistency; technical snippets can use Codex
  design review)
- tester: off (no runnable product here; acceptance is a manual dry-run of the /hr-ceo flow)

## Explainer (the /hr-explainer role, standalone)
- Output language: match the user

## Model split
- CEO: Claude (reads ceo-brain.md)
- Coder/Drafter: Claude Sonnet by default; escalate to Opus if Sonnet fails twice on the
  same spot. Never Haiku.
- Reviewer/Editor: Codex CLI or a second tool

## File locations
- Style: .ai-team/style.md
- Commit style: .ai-team/commit.md
- CEO brain: skills/hr-ceo/templates/ceo-brain.md (this repo maintains that default brain itself)
- Review reports: .ai-team/reviews/ (git-ignored)
- Test reports: .ai-team/tests/ (git-ignored)
