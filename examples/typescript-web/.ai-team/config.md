# .ai-team master settings — EXAMPLE (TypeScript / React web app)

> A filled-in example for a code project. Copy/adapt into your own `.ai-team/config.md`.

## Project
- Name: acme-dashboard
- Default task type: code

## Language (two separate choices — confirm each, never assume they match)
- Conversation language: match the user
- Artifact language: English   ← prd.md / sdd.md / plan.md / reviews / tests
> Chatting in one language does not mean the docs are written in it. Code comments and
> README/commit prose are set separately in `style.md`.

## Enabled roles
- coder: on
- reviewer: on
- tester: on

## Explainer (the /hr-explainer role, standalone)
- Output language: match the user

## Model split (dual-model review)
- CEO: Claude (reads ceo-brain.md)
- Coder: Claude Sonnet by default; escalate to Opus if Sonnet fails twice on the same spot.
  Never Haiku.
- Reviewer: Codex CLI (`codex review` / `codex exec`)
- Tester: Claude + Playwright-MCP

## File locations
- Spec: .ai-team/prd.md
- Design: .ai-team/sdd.md
- Plan: .ai-team/plan.md
- Review reports: .ai-team/reviews/
- Test reports: .ai-team/tests/
- Style: .ai-team/style.md
- Commit style: .ai-team/commit.md
- CEO brain: .ai-team/ceo-brain.md
- Long-term memory: .ai-team/memory.md
- Guardrails: .ai-team/guardrails.md

## Recovery policy (exception handling — thresholds before escalating)
- Code-review loop: max 3 CHANGES_REQUESTED rounds on the same batch, then the CEO escalates
  the Coder to Opus / reopens the SDD / stops for the human.
- Coder escalation: Sonnet → Opus after 2 failures on the same task.
- Tester failure: blocking scenarios go back to the CEO, never marked passed.

## Gates (require human confirmation to proceed)
- After the SDD design review.
- When the code-review loop hits the Recovery-policy max rounds.
- Before any action listed in `guardrails.md`.
