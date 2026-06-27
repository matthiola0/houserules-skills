# .ai-team 設定總表

> CEO 在 init 時依你的回答生成這份檔。之後每次都先讀它。可隨時手動編輯。
> `<...>` 是待填欄位。

## 專案
- 名稱：<專案名>
- 預設任務型態：code  | writing | research   ← 擇一作為預設

## 啟用的角色
- coder：on
- reviewer：on
- tester：on

## 模型分工（雙模型互審）
- CEO：Claude（讀 ceo-brain.md）
- Coder：Claude
- Reviewer：Codex CLI（`codex review` / `codex exec`）
- Tester：Claude + MCP

## 檔案位置
- 規格：.ai-team/prd.md
- 設計：.ai-team/sdd.md（非代碼：outline.md）
- 計畫：.ai-team/plan.md
- 審查報告：.ai-team/reviews/
- 測試報告：.ai-team/tests/
- 風格：.ai-team/style.md
- commit 風格：.ai-team/commit.md
- CEO 大腦：.ai-team/ceo-brain.md

## 關卡（需人類確認才放行）
- SDD / outline 設計審查後
- 代碼審查 CHANGES_REQUESTED 累計過多時
