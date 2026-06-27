# Swapping the CEO brain (nuwa-skill)

The CEO's thinking is set by `.ai-team/ceo-brain.md`, defaulting to **Elon Musk
first-principles**. To have the CEO brainstorm with you using another person's decision
framework, distill that person's "cognitive OS" with
[nuwa-skill](https://github.com/alchaincyf/nuwa-skill) and replace this file. The coupling
is **loose**: the CEO runs fine without nuwa (it has a default brain); nuwa just enhances it.

## Steps

1. Install nuwa:
   ```bash
   npx skills add alchaincyf/nuwa-skill
   ```
2. Distill the person you want (nuwa runs multi-stream research and generates a
   cognitive framework in SKILL.md format):
   ```
   distill <person name>
   ```
3. Paste nuwa's output into `.ai-team/ceo-brain.md`, **replacing the whole file**.
   Recommended: keep the two sections from our template's end:
   - "How to apply to this CEO role" — map the person's thinking to PRD/SDD/dispatch/gates.
   - "Honest limitations" — a reminder that this is a public-info approximation and that the
     style doesn't fit every context.
4. The next `/ceo` will use the new brain.

## Notes
- `ceo-brain.md` is a **lens / decision framework**, not role-play — the goal is a different
  way of "thinking about problems," not just imitating a tone.
- Different people fit different tasks: Musk-style deletion for execution/hardware; for
  product experience or research rigor, swap in a more fitting framework. You can keep a
  different `ceo-brain.md` per project.
- To keep multiple brains: store several under `.ai-team/brains/` (e.g. `musk.md`,
  `jobs.md`) and copy whichever you want into `ceo-brain.md`.
