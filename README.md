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
| **CEO** (`/ceo`) | Claude (swappable brain, defaults to a Musk first-principles framework) | Brainstorms with you, produces the PRD/SDD/Plan, dispatches work, reports back. The only role you talk to. |
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

## Default mode

What you get out of the box, with zero customization:

- **Roles**: CEO + Coder + Reviewer + Tester, all on. You talk only to the CEO.
- **Models**: Claude writes (CEO, Coder, Tester); **Codex CLI reviews** — a different model,
  so review is stricter (dual-model review).
- **CEO brain**: Elon Musk first-principles framework (`ceo-brain.md`), swappable.
- **Flow (code)**: brainstorm → PRD → SDD → **design-review gate (must pass + you confirm
  before any code)** → plan → code → code-review loop until `PASS` → scenario tests → report.
- **Brainstorming**: the CEO asks you multiple-choice questions instead of open prompts.
- **Commit style**: Conventional Commits prefix on (`feat:`/`fix:`/…), imperative subject,
  **no `Co-Authored-By` / AI attribution**, no emojis.
- **Code style**: "new code reads like existing code" is the top rule; other fields are
  asked during init.
- **First run (init)**: with no `.ai-team/`, the CEO runs a short Q&A, writes
  `config/style/commit/ceo-brain.md` into the project's `.ai-team/`, and adds `.ai-team/`
  to the project's root `.gitignore` (local-only by default).
- **Non-code tasks**: roles auto-swap to Drafter / Editor / Fact-checker; the SDD becomes
  an `outline.md`. Same flow.
- **Messaging**: all roles communicate through files under `.ai-team/`; `plan.md`
  checkboxes are the progress board.

In one line: **Claude writes, Codex reviews, a Musk-style brain orchestrates; design must
pass before any code; commits are clean with no AI attribution; set it once and reuse
across projects.**

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

By default the CEO uses a Musk first-principles framework. To use someone else's, distill
their cognitive framework with [nuwa-skill](https://github.com/alchaincyf/nuwa-skill)
and paste it into `.ai-team/ceo-brain.md`. See
[docs/nuwa-integration.md](docs/nuwa-integration.md).

---

## License

MIT
