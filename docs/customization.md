# Customization guide

`houserules-skills` uses a **two-layer** design so the same skills are reusable across
projects yet customizable per project.

```
Skill body (defaults, don't edit after install)   Project layer (.ai-team/, per project, git-ignored by default, overrides)
skills/ceo|coder|reviewer|tester/SKILL.md          .ai-team/config.md      ← which roles, models
skills/ceo/templates/ (used by init)               .ai-team/style.md       ← code/writing style
                                                   .ai-team/commit.md      ← commit style
                                                   .ai-team/ceo-brain.md   ← CEO thinking
```

On init the CEO adds `.ai-team/` to your project's **root** `.gitignore`, so the whole
team working directory is local-only by default and stays out of version control.

**Principle**: the workflow and personas come from the skills (stable); the "rules" —
style, commit, CEO brain — come from the project layer (variable). You **set it once**, and
the CEO reads it automatically every time, so you never re-explain it verbally.

## Common customizations

### Change code / commit style
Edit `.ai-team/style.md` and `.ai-team/commit.md` directly. The Coder / Reviewer follow it
next time automatically. For complete filled-in references, see
[`examples/`](../examples/) (a TypeScript/React code project) and this repo's own
`.ai-team/` (a writing project).

### Toggle roles
Edit "Enabled roles" in `.ai-team/config.md`. For example, a pure-research project can turn
off `tester` and use fact-check mode instead.

### Swap the CEO brain
Replace `.ai-team/ceo-brain.md`. The default is Musk; to use someone else see
[nuwa-integration.md](nuwa-integration.md).

### Tweak role behavior / rename skills
- To fine-tune how a role works: drop a supplement like `coder.overrides.md` into
  `.ai-team/` and note it in `config.md`; the CEO will pass it along when dispatching.
- If a command name like `/ceo` collides with your other skills: rename the `name` in
  `skills/<role>/SKILL.md` frontmatter and the folder (e.g. `hr-ceo`), and update the
  dispatch references in the CEO SKILL.md accordingly.

## Cross-project reuse

1. One-time: `npx skills add <your-account>/houserules-skills` (global install).
2. Each new project: `/ceo` → first run walks init to generate that project's `.ai-team/`.
3. By default `.ai-team/` is git-ignored (local-only), so each project / machine regenerates
   it via init. If instead you want to **share** the same rules across machines or a team,
   remove the `.ai-team/` line from `.gitignore` and commit the config files
   (`config.md`, `style.md`, `commit.md`, `ceo-brain.md`); you can keep `reviews/` and
   `tests/` ignored.
