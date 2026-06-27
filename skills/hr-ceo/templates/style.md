# Code style (house rules) — recommended defaults

> These are sensible, language-agnostic defaults so init can be skipped with one choice.
> Pick "Customize" at init to pin specifics. A worked example with concrete values:
> `examples/typescript-web/.ai-team/style.md`.

## General
- New code must read like the existing code; follow the file/project conventions first.
- Clear > clever. Plain names, no pointless abbreviations.
- No dead code, no commented-out code.

## Language / framework
- Auto-detect the stack from the project (package.json / pyproject.toml / go.mod / Cargo.toml
  ...) and follow that language's idioms.
- Formatter: the project's configured formatter is the source of truth (Prettier / Black /
  gofmt / rustfmt). If none exists, add the standard one for the stack.
- Linter: the project's linter; no new warnings on commit.

## Naming / formatting
- Follow the language's conventional style (e.g. camelCase in JS/TS, snake_case in Python)
  and whatever the formatter emits. Don't hand-format around the formatter.

## Tests
- Add tests for new behavior (happy path + key edge cases) with the project's test framework.

## Error handling
- Validate external input at boundaries; never swallow errors silently.

## Comments (in code)
- Explain why, not what; match the density of surrounding code.
- Doc-comments on exported/public APIs (JSDoc / docstring / rustdoc as the stack dictates).
- TODO/FIXME format: `// TODO(owner): ...`

## Documentation & prose (README, docs, commit bodies)
- Concise, direct, second person; no marketing fluff.
- Lead with the why; short sections; tables for structured info.
- Code / paths / commands in `backticks`; copy-pasteable fenced blocks; sentence-case headings.
- Keep docs in sync with behavior — update them in the same change.
