# houserules-skills

> Set your rules once, stop repeating them. A reusable AI agent team for Claude Code.

Tired of re-explaining your code style, commit format, and workflow to the AI on every
new project? `houserules-skills` packages a small **AI agent team** as installable Claude
Code skills. You set your "house rules" once; every project applies them automatically and
the quality stays consistent.

Inspired by George Xing's *How I build with AI as a 1-person company* (a brainstorm → plan
→ build → review loop with **dual-model review**), plus an explicit **CEO** that
orchestrates everything.

---

## What it is

A team of four roles. **You only ever talk to the CEO** — it dispatches the rest:

| Role | Powered by | What it does |
|------|-----------|--------------|
| **CEO** (`/hr-ceo`) | Claude | Brainstorms with you, writes the PRD + design, plans the work, dispatches the team, reports back. |
| **Coder** (`/hr-coder`) | Claude | Implements the plan and commits, following your style. |
| **Reviewer** (`/hr-reviewer`) | **Codex (a different model)** | Reviews the design and the code. A *different* model catches what the author misses. |
| **Tester** (`/hr-tester`) | Claude + tools | Runs the real product against your scenarios. |
| **Explainer** (`/hr-explainer`) | Claude (Paul Graham brain) | *Standalone.* Explains any project in plain language — an intro doc, or Q&A about a repo. |

For writing/research tasks the first three roles switch to **Drafter / Editor /
Fact-checker** automatically. The **Explainer** is standalone — call `/hr-explainer`
yourself whenever you want a plain-language intro or answers about a project.

---

## How it works

```
You ▶ CEO ─brainstorm→ prd.md
         ─design→     sdd.md ──(Reviewer checks the design)──┐ must pass first
         ─plan→       plan.md                                │
                        ▼                                     │
                   Coder ─writes + commits→ code              │
                        ▼                                     │
                   Reviewer ─reviews the code→ (fix loop until it passes)
                        ▼
                   Tester ─runs your scenarios→ report
                        ▼
                   CEO sums up for you
```

Roles talk to each other through plain files in a `.ai-team/` folder — nothing hidden.

---

## Design patterns it maps to

This team isn't ad-hoc — it lines up with the agentic design patterns catalogued in Antonio
Gulli's *Agentic Design Patterns* (the widely-shared ~400-page Google guide). The ones this
project already implements:

| Pattern | Where it lives here |
|---------|---------------------|
| **Multi-Agent Collaboration** | Four specialized roles instead of one do-everything agent. |
| **Routing** | The CEO dispatches each task to the right role. |
| **Planning** | The CEO decomposes work into `prd.md` → `sdd.md` → `plan.md` before any code. |
| **Reflection** | The Reviewer critiques the design and the code — **via a different model (Codex)**, so blind spots differ. |
| **Inter-Agent Communication** | Roles hand off through plain files in `.ai-team/` — auditable, nothing hidden. |
| **Human-in-the-Loop** | You only talk to the CEO, which pauses at each gate for your call. |
| **Goal Decomposition & Prioritization** | `plan.md` carries priorities + dependencies; the CEO schedules ready tasks, not blindly top-to-bottom. |
| **Memory Management** | `memory.md` is long-term memory — conventions and decisions that persist across tasks so the team stops relearning. |
| **Goal Setting & Evaluation** | Every PRD scenario has a measurable acceptance criterion; the Tester returns a scored scorecard. |
| **Exception Handling & Recovery** | A Recovery policy bounds the review/fix loop — escalate, reopen the design, or stop, never loop forever. |
| **Guardrails** | `style.md` / `commit.md` plus `guardrails.md` (forbidden ops + confirm-before-acting) constrain every role's output. |

---

## Install

```bash
npx skills add matthiola0/houserules-skills
```

You need:
- **Claude Code** (CEO / Coder / Tester)
- **Codex CLI** >= 0.124 for the Reviewer — `codex` must run in your terminal
  (`npm i -g @openai/codex`, then `codex login`)
- *(optional)* `gemini-cli` for research; Playwright-MCP for browser tests

The four skills install as `hr-ceo` / `hr-coder` / `hr-reviewer` / `hr-tester`. If a name
collides with a skill you already have, see [Rename the skills](#rename-the-skills).

---

## Quick start

1. Open Claude Code in your project folder.
2. Type **`/hr-ceo`** and say what you want to build.
3. The first time, it asks just two things — your task type, and **"use recommended rules
   or customize?"**. Pick recommended and it's ready instantly.
4. The CEO then walks the team through brainstorm → design → build → review → test, pausing
   at each gate so you stay in control.

---

## What you get by default

- **All four roles on.** Claude writes; **Codex reviews** (stricter, because it's a
  different model).
- **Cost-aware model tiers.** The Coder runs as **Sonnet** by default and only escalates a
  task to **Opus** if Sonnet fails twice on the same spot. (No Haiku.)
- **CEO thinks in Elon Musk first-principles** (delete needless requirements, demand
  evidence). Swappable.
- **Design must pass review before any code is written.**
- **Acceptance criteria + scorecard.** Every PRD scenario gets a measurable pass/fail bar; the
  Tester reports a scored scorecard, not a vibe check.
- **Bounded recovery.** The review→fix loop can't spin forever — at the threshold the CEO
  escalates the Coder to Opus, reopens the design, or stops for you.
- **Safety guardrails + long-term memory.** `guardrails.md` blocks destructive actions
  (force-push, prod writes, secret commits) and pauses for confirmation; `memory.md` remembers
  this repo's conventions and decisions so the team doesn't relearn them every task.
- **Commits**: Conventional Commits (`feat:` / `fix:` …), imperative, **no "Co-Authored-By"
  or AI attribution**, no emojis.
- **Code style auto-detects your stack** (Prettier/Black/gofmt…), comments and docs default
  to English.
- **`.ai-team/` is git-ignored** (local to each project) unless you choose to share it.

---

## Customize it — the cookbook

Everything is plain Markdown in your project's **`.ai-team/`** folder. To change a rule,
open the file and edit the line. The CEO re-reads these on every run, so **you set it once
and never repeat yourself.**

| I want to change… | Open this file | Edit this |
|-------------------|----------------|-----------|
| Code style (language, formatter, naming, tests) | `.ai-team/style.md` | the `Language / framework`, `Naming`, `Tests` sections |
| Comment style | `.ai-team/style.md` | the `Comments (in code)` section |
| **Comment language** | `.ai-team/style.md` | the `Comment language:` line |
| **Documentation language** | `.ai-team/style.md` | the `Prose language:` line |
| Commit message style | `.ai-team/commit.md` | the `Format` section / the `Toggle` |
| The CEO's way of thinking | `.ai-team/ceo-brain.md` | replace the whole file |
| Which roles run / the flow | `.ai-team/config.md` | the `Enabled roles` section |
| Recovery thresholds (how many review rounds before escalating) | `.ai-team/config.md` | the `Recovery policy` section |
| **Safety guardrails** (forbidden ops, confirm-before actions) | `.ai-team/guardrails.md` | the two lists |
| **Long-term memory** (repo conventions, past decisions) | `.ai-team/memory.md` | append entries (the team also fills this) |
| The Explainer's output language | `.ai-team/config.md` | the `Explainer` section's `Output language` line |
| How the Explainer writes | `.ai-team/explainer-brain.md` | replace the whole file |

Concrete recipes:

### Change the code style
Open `.ai-team/style.md`. Example — switch the project to Python with Black:
```
## Language / framework
- Primary language: Python 3.12
- Formatter: Black (its output is the source of truth)
- Linter: Ruff
```
Next time the Coder writes code and the Reviewer checks it, both follow this.

### Change the commit style
Open `.ai-team/commit.md`.
- **Turn Conventional Commits off** (use plain `Add retry to upload client` instead of
  `feat: add retry…`): find the `## Toggle` section and set the prefix to **off**.
- The "never add AI attribution / no emojis" rules live under `## Hard rules` — keep or
  edit them there.

### Change the comment style or language
Open `.ai-team/style.md`, the `## Comments (in code)` section. Example — write comments in
Traditional Chinese and require doc-comments:
```
## Comments (in code)
- Comment language: Traditional Chinese (繁體中文).
- Doc-comments on every exported function (JSDoc).
- TODO/FIXME format: // TODO(yourname): ...
```

### Change the documentation language
Open `.ai-team/style.md`, the `## Documentation & prose` section. Example:
```
## Documentation & prose (README, docs, commit bodies)
- Prose language: Traditional Chinese (繁體中文); keep code, commands, and filenames in English.
```

### Swap the CEO's brain (e.g. Steve Jobs instead of Musk)
The CEO's thinking lives in `.ai-team/ceo-brain.md`. Either edit it directly, or generate a
new one with [nuwa-skill](https://github.com/alchaincyf/nuwa-skill):
```bash
npx skills add alchaincyf/nuwa-skill
# then in Claude Code:  distill Steve Jobs
```
Paste the result into `.ai-team/ceo-brain.md`. Full guide:
[docs/nuwa-integration.md](docs/nuwa-integration.md).

### Explain a project in plain language
Call `/hr-explainer` in any repo. It reads the README / specs / code and either writes a
plain intro (what it is, the problem it solves, who it's for, how to start) or answers your
questions — no jargon, no marketing words, no weird metaphors. Set its language in
`.ai-team/config.md`:
```
## Explainer (the /hr-explainer role, standalone)
- Output language: Traditional Chinese (繁體中文)
```
If you don't set it, it replies in whatever language you ask in. To change *how* it writes,
edit `.ai-team/explainer-brain.md` (defaults to a Paul Graham clear-writing style).

### Turn a role off (change the flow)
Open `.ai-team/config.md`, the `## Enabled roles` section. Example — a quick script where
you don't want the test stage:
```
## Enabled roles
- coder: on
- reviewer: on
- tester: off
```
Turn `reviewer: off` if you want to skip the dual-model review entirely (not recommended —
it's the best part).

### Rename the skills
If `/hr-ceo` etc. clash with other skills, rename the folder and the `name:` line in each
`skills/<role>/SKILL.md` (e.g. to your own prefix), and update the dispatch references in
`skills/hr-ceo/SKILL.md`. See [docs/customization.md](docs/customization.md).

---

## Why it's reusable (two layers)

- **The skills** (installed once, globally) hold the *workflow and the roles* — stable, you
  don't touch them.
- **`.ai-team/`** (per project) holds *your rules* — style, commits, CEO brain. This is what
  you customize.

Same team everywhere; different rules per project. See filled-in examples in
[`examples/`](examples/) (a TypeScript/React project) and this repo's own
[`.ai-team/`](.ai-team/) (a writing project).

To **share** one set of rules across machines or a team, just commit `.ai-team/` (remove its
line from `.gitignore`).

---

## License

MIT
