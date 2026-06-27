# Commit 訊息風格 — houserules-skills 本專案（live）

> 本 repo 自己遵守的 commit 規矩。git 歷史就是照這份寫的。

## 硬規則（不可違反）
- **絕不**加 `Co-Authored-By` 或任何 AI / Claude / Codex 署名與工具簽名。
- 不加表情符號、不加廣告行（如「Generated with ...」）。

## 格式
- 主旨：祈使句（imperative）、≤ 50 字、句首大寫、句尾不加句號。
  - 好：`Add reviewer skill with Codex code-review mode`
  - 壞：`added reviewer`、`update stuff`
- 主旨後空一行，再寫 body（非必要可省）。body 說明 what / why，不逐行複述 diff。
- 一個 commit 一件事。

## 範例（取自本 repo 首個 commit）
```
Add houserules-skills AI agent team skill pack

Four-role team (CEO/Coder/Reviewer/Tester) as installable Claude Code
skills. CEO orchestrates a brainstorm -> PRD -> SDD -> ... loop; Reviewer
runs on Codex CLI for dual-model review. ...
```

## 本專案慣例
- Conventional Commits 前綴：off（保持純祈使句風格）。
