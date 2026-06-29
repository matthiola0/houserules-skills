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

## Language (two separate choices — confirm each, never assume they match)
- Conversation language: match the user
- Artifact language: English   ← skill files, docs, and specs are written in English even
  when the conversation is in another language
> The chat language is not automatically the artifact language; confirm each separately.
> Code comments and README/commit prose are set separately in `style.md`.

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

## Concurrency (parallel dispatch)
- **Max parallel Coders**: 3   ← how many ready, file-disjoint tasks run at once
- Only parallelize tasks (here: independent skill/doc files) that touch **disjoint files**
  and share no ordering. Tasks that edit the same file, or where one's output feeds another,
  run **serially**. When in doubt, serialize.
- Isolation: file-disjoint tasks share the working tree; tasks that must touch overlapping
  areas (or each commit on their own) run in separate **git worktrees**, merged after.

## File locations
- Style: .ai-team/style.md
- Commit style: .ai-team/commit.md
- CEO brain: skills/hr-ceo/templates/ceo-brain.md (this repo maintains that default brain itself)
- Long-term memory: .ai-team/memory.md
- Guardrails: .ai-team/guardrails.md
- Review reports: .ai-team/reviews/ (git-ignored)
- Test reports: .ai-team/tests/ (git-ignored)

## Recovery policy
- Editor/review loop: max 3 CHANGES_REQUESTED rounds on the same draft, then the CEO
  escalates to Opus / reopens the outline / stops for the human.

## Gates (require human confirmation to proceed)
- After the outline/design review.
- When the review loop hits the Recovery-policy max rounds.
- Before any action listed in `guardrails.md`.
