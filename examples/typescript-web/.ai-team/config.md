# .ai-team master settings — EXAMPLE (TypeScript / React web app)

> A filled-in example for a code project. Copy/adapt into your own `.ai-team/config.md`.

## Project
- Name: acme-dashboard
- Default task type: code

## Enabled roles
- coder: on
- reviewer: on
- tester: on

## Model split (dual-model review)
- CEO: Claude (reads ceo-brain.md)
- Coder: Claude
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

## Gates (require human confirmation to proceed)
- After the SDD design review
- When code-review CHANGES_REQUESTED accumulates 3+ rounds
