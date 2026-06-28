# Guardrails (safety house rules)

> Output guardrails every role obeys. The CEO loads this every run; the Coder and Tester
> must **stop and get explicit human confirmation** before any action listed here. Edit the
> lists to fit your project. When in doubt, ask — don't act.

## Forbidden — never do these
(No override unless the human types the command/approval themselves.)
- Force-push (`git push --force`) to a shared branch, or any history rewrite on `main`.
- `git reset --hard` / `git clean -fd` that discards uncommitted human work.
- Deleting files or directories outside the current task's scope; bulk or recursive deletes.
- Committing secrets (`.env`, keys, tokens) or printing them to logs / reports.
- Disabling tests or CI, or weakening security/validation, just to make something "pass".

## Require human confirmation before proceeding (pause and ask)
- Pushing to a remote; opening, merging, or closing a PR.
- Any write to production / staging, prod databases, or live infrastructure.
- Schema migrations, data deletes/backfills — anything not easily reversible.
- Installing new dependencies, or changing the build / release / deploy pipeline.
- Spending money or calling paid external APIs at scale.

## How roles honor this
- **Coder**: before any action above, stop, state exactly what you intend to run, and ask
  the CEO/human. Never assume a prior "yes" extends to a new action.
- **Tester**: never run destructive setup against real data — use a throwaway/local
  environment. Reads here before driving the product.
- **CEO**: surface guardrail hits to the human at the gate, and record any approved override
  (what + why) in `memory.md`.
