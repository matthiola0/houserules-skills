# 客製化指南

`houserules-skills` 採**兩層**設計，讓同一套 skill 跨專案重用、又能各自客製。

```
skill 本體（出廠預設，安裝後不要改）        專案層（.ai-team/，隨專案走、可覆蓋）
skills/ceo|coder|reviewer|tester/SKILL.md   .ai-team/config.md      ← 啟用哪些角色、模型
templates/ (init 用的模板)                  .ai-team/style.md       ← 代碼/寫作風格
                                            .ai-team/commit.md      ← commit 風格
                                            .ai-team/ceo-brain.md   ← CEO 思維
```

**原則**：流程與人設由 skill 提供（穩定）；風格、commit、CEO 大腦等「規矩」由專案層
設定提供（可變）。你**設定一次**，CEO 之後每次自動讀取，不必再口頭交代。

## 常見客製

### 改代碼 / commit 風格
直接編輯 `.ai-team/style.md`、`.ai-team/commit.md`。下次 Coder / Reviewer 自動遵守。

### 開關角色
編輯 `.ai-team/config.md` 的「啟用的角色」。例如純研究專案可關掉 `tester` 換 fact-check 模式。

### 換 CEO 大腦
覆蓋 `.ai-team/ceo-brain.md`。預設是馬斯克；換別人見 [nuwa-integration.md](nuwa-integration.md)。

### 改角色行為 / 重新命名 skill
- 想微調某角色的做事方式：在 `.ai-team/` 放一份 `coder.overrides.md` 之類的補充說明，
  並在 `config.md` 註明，CEO 派活時會一併傳給該角色。
- `/ceo` 等指令名若與你其他 skill 衝突：重新命名 `skills/<role>/SKILL.md` frontmatter 的
  `name` 與資料夾名（例如 `hr-ceo`），並同步更新 CEO SKILL.md 裡的調度引用。

## 跨專案重用流程
1. 一次性：`npx skills add <你的帳號>/houserules-skills`（全域安裝）。
2. 每個新專案：`/ceo` → 第一次跑 init 生成該專案的 `.ai-team/`。
3. 把 `.ai-team/config.md`、`style.md`、`commit.md`、`ceo-brain.md` **提交進版控**，
   團隊 / 未來的你就共用同一套規矩。`reviews/`、`tests/` 可視需要加進 `.gitignore`。
