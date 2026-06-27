# houserules-skills

> Set your rules once, stop repeating them. A reusable AI agent team for Claude Code.

`houserules-skills` packages a "one-person company / AI agent team" as installable
Claude Code Skills. The goal is simple: **stop re-explaining your code style, commit
style, and workflow to the AI on every project.** Set your house rules once, have every
project apply them automatically, and keep quality stable.

Inspired by George Xing's *How I build with AI as a 1-person company* (a brainstorm →
plan → execute → review workflow with dual-model review), plus an explicit **CEO
orchestrator** role.

---

## What it is

A team of four roles. You talk only to the **CEO**; it dispatches the rest:

| Role | Powered by | Responsibility |
|------|-----------|----------------|
| **CEO** (`/ceo`) | Claude (swappable brain, defaults to a first-principles framework) | Brainstorms with you, produces the PRD/SDD/Plan, dispatches work, reports back. The only role you talk to. |
| **Coder** (`/coder`) | Claude | Implements the SDD/Plan and commits per your style. |
| **Reviewer** (`/reviewer`) | **Codex (a different model)** | Design review + code review, structured reports, loops until it passes. |
| **Tester** (`/tester`) | Claude + MCP | Runs real user-scenario tests / fact-checks. |

**Dual-model review:** Claude writes, Codex reviews. Different models have different
blind spots, so review is stricter.

For non-code tasks (writing / research), the CEO automatically swaps the roles to
**Drafter / Editor / Fact-checker** — same workflow, different personas.

---

## Workflow

```
You ▶ CEO ─brainstorm→ prd.md
         ─design→     sdd.md ──(Reviewer design review)──┐ must pass to continue
         ─break down→ plan.md                            │
                       ▼                                  │
                  Coder ─write + commit→ code             │
                       ▼                                  │
                  Reviewer ─code review→ reviews/  ─(loop until fixed)
                       ▼
                  Tester ─scenario tests→ tests/
                       ▼
                  CEO reports back to you
```

Roles pass messages through files under `.ai-team/` (traceable, tool-agnostic).

---

## Install

```bash
npx skills add <your-account>/houserules-skills
```

Requirements:
- **Claude Code** (CEO / Coder / Tester)
- **Codex CLI** ≥ 0.124 (Reviewer) — `codex` runnable in your terminal
- (optional) **gemini-cli** (research / fact-check tasks)
- (optional) Playwright-MCP / XcodeBuildMCP (Tester running web / iOS tests)

The installer (vercel-labs/skills) scans the `skills/` catalog layout and installs each
role as its own skill.

---

## Quick start

1. Open Claude Code in your project directory.
2. Type `/ceo` and describe what you want to build.
3. On first run it walks an **init Q&A** and generates your settings under `.ai-team/`
   (style, commit, CEO brain).
4. The CEO then runs the whole team through brainstorm → design → build → review → test.

---

## Customization (two layers)

The skill body ships fixed defaults; your per-project settings under `.ai-team/` travel
with the project and override them:

| File | Purpose |
|------|---------|
| `.ai-team/config.md` | Master switch: which roles are on, models, task type |
| `.ai-team/style.md` | Code style |
| `.ai-team/commit.md` | Commit message style |
| `.ai-team/ceo-brain.md` | CEO's thinking framework (swappable) |

See [docs/customization.md](docs/customization.md).

## Swapping the CEO brain (nuwa)

By default the CEO uses a first-principles framework. To use someone else's, distill
their cognitive framework with [nuwa-skill](https://github.com/alchaincyf/nuwa-skill)
and paste it into `.ai-team/ceo-brain.md`. See
[docs/nuwa-integration.md](docs/nuwa-integration.md).

---

## License

MIT
