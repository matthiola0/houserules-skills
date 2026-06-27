# .ai-team 設定總表 — houserules-skills 本專案

> 這是本 repo 自己的活設定（dogfooding）：houserules-skills 就是用這套規矩開發的。
> 同時也是新使用者的填寫範例——對照 templates/ 的空白模板看，就知道填好後長怎樣。

## 專案
- 名稱：houserules-skills
- 預設任務型態：writing（本 repo 內容是 Markdown skill 檔與文件，非編譯型代碼）

## 啟用的角色
- coder：on（這裡的「代碼」= skill / 文件撰寫，對應 Drafter 模式）
- reviewer：on（Editor 模式審措辭與一致性；技術片段可用 Codex 設計審查）
- tester：off（本 repo 無可執行產品；改以人工 dry-run /ceo 流程驗收）

## 模型分工
- CEO：Claude（讀 ceo-brain.md）
- Coder/Drafter：Claude
- Reviewer/Editor：Codex CLI 或第二工具

## 檔案位置
- 風格：.ai-team/style.md
- commit 風格：.ai-team/commit.md
- CEO 大腦：templates/ceo-brain.md（本 repo 維護的就是這顆預設大腦本身）
- 審查報告：.ai-team/reviews/（git 忽略）
- 測試報告：.ai-team/tests/（git 忽略）
