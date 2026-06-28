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

## Concurrency (parallel dispatch)
- **Max parallel Coders**: 3   ← how many ready, file-disjoint tasks run at once
- Only parallelize tasks that touch **disjoint files** and share no schema/migration or
  hidden ordering. Tasks that edit the same files, or where one's output feeds another,
  run **serially**. When in doubt, serialize.
- Isolation: file-disjoint tasks share the working tree; tasks that must touch overlapping
  areas (or each commit on their own) run in separate **git worktrees**, merged after.

## File locations
- Spec: .ai-team/prd.md
- Design: .ai-team/sdd.md (non-code: outline.md)
- Plan: .ai-team/plan.md
- Review reports: .ai-team/reviews/
- Test reports: .ai-team/tests/
- Style: .ai-team/style.md
- Commit style: .ai-team/commit.md
- CEO brain: .ai-team/ceo-brain.md
- Long-term memory: .ai-team/memory.md   ← conventions + decisions, persists across tasks
- Guardrails: .ai-team/guardrails.md     ← forbidden ops + confirm-before-acting list

## Recovery policy (exception handling — thresholds before escalating)
- **Code-review loop**: if the Reviewer returns CHANGES_REQUESTED **3×** on the same batch,
  stop looping and the CEO decides — implementation issue → escalate the Coder to Opus and
  retry once; design issue → reopen the SDD (back to design review); still stuck → stop and
  ask the human. (max rounds: 3)
- **Coder escalation**: Sonnet → Opus after **2** failures on the same task (see Model split).
- **Tester failure**: failing scenarios go back to the CEO, who returns them to the Coder or
  adjusts the PRD — never silently marked passed.
- **Blocked / wrong SDD**: the Coder stops and reports; it does not redesign on its own.

## Gates (require human confirmation to proceed)
- After the SDD / outline design review.
- When the code-review loop hits the Recovery-policy max rounds.
- Before any action listed in `guardrails.md`.
