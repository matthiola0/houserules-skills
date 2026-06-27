# 風格 — houserules-skills 本專案（live）

> 本 repo 的內容是 Markdown（SKILL.md、文件、模板），所以「代碼風格」這裡指**撰寫風格**。

## 撰寫原則
- 清楚 > 花俏。一句講一件事，能刪的字就刪（呼應 ceo-brain 的「刪除優先」）。
- 中文為主，技術名詞 / 指令 / 檔名保留英文原文。
- 指令、路徑、檔名一律用反引號標出（如 `.ai-team/commit.md`、`codex review`）。

## SKILL.md 慣例
- frontmatter 必含 `name`（lowercase-hyphen，與資料夾同名）與 `description`。
- `description` 寫清楚「何時該用這個 skill」，因為這是被自動選用的依據。
- 正文用編號小節（§）+ 明確步驟，讓被調度的角色照做不需臆測。

## 文件慣例
- 表格用來對照「角色 / 檔案 / 職責」這類結構化資訊。
- 範例一律給可直接複製的 fenced code block。
- 跨檔引用用相對路徑連結（如 `[customization.md](docs/customization.md)`）。

## 一致性
- 角色名統一：CEO / Coder / Reviewer / Tester（非代碼版：Drafter / Editor / Fact-checker）。
- 產出物名統一：`prd.md` / `sdd.md`（或 `outline.md`）/ `plan.md` / `reviews/` / `tests/`。
