# .ai-team master settings

> The CEO generates this during init from your answers. It is read first every time.
> Edit it any time. `<...>` marks a field to fill in.
> A complete filled example: `examples/typescript-web/.ai-team/config.md`.

## Project
- Name: <project name>
- Default task type: code | writing | research   ← pick one as the default

## Enabled roles
- coder: on
- reviewer: on
- tester: on

## Explainer (the /hr-explainer role, standalone)
- Output language: match the user   ← or pin one, e.g. "Traditional Chinese (繁體中文)"

## Model split (dual-model review)
- CEO: Claude (reads ceo-brain.md)
- Coder: Claude Sonnet by default; escalate that task to Opus if Sonnet fails twice on the
  same spot. Never Haiku.
- Reviewer: Codex CLI (`codex review` / `codex exec`)
- Tester: Claude + MCP

## File locations
- Spec: .ai-team/prd.md
- Design: .ai-team/sdd.md (non-code: outline.md)
- Plan: .ai-team/plan.md
- Review reports: .ai-team/reviews/
- Test reports: .ai-team/tests/
- Style: .ai-team/style.md
- Commit style: .ai-team/commit.md
- CEO brain: .ai-team/ceo-brain.md

## Gates (require human confirmation to proceed)
- After the SDD / outline design review
- When code-review CHANGES_REQUESTED accumulates too many rounds
