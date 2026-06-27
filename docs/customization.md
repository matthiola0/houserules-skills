# Customization guide

`houserules-skills` uses a **two-layer** design so the same skills are reusable across
projects yet customizable per project.

```
Skill body (defaults, don't edit after install)   Project layer (.ai-team/, travels with the project, overrides)
skills/ceo|coder|reviewer|tester/SKILL.md          .ai-team/config.md      ← which roles, models
templates/ (used by init)                          .ai-team/style.md       ← code/writing style
                                                   .ai-team/commit.md      ← commit style
                                                   .ai-team/ceo-brain.md   ← CEO thinking
```

**Principle**: the workflow and personas come from the skills (stable); the "rules" —
style, commit, CEO brain — come from the project layer (variable). You **set it once**, and
the CEO reads it automatically every time, so you never re-explain it verbally.

## Common customizations

### Change code / commit style
Edit `.ai-team/style.md` and `.ai-team/commit.md` directly. The Coder / Reviewer follow it
next time automatically.

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
3. Commit `.ai-team/config.md`, `style.md`, `commit.md`, `ceo-brain.md` into version
   control, so your team / future-you share the same rules. `reviews/` and `tests/` can be
   added to `.gitignore` as needed.
