# houserules-skills

> 設定一次，之後不用每次重講。一套可跨專案重用的 AI Agent 團隊。

`houserules-skills` 把「一人公司 / AI Agent 團隊」做成一包可安裝的 Claude Code Skills。
核心目的很簡單：**不要每次都重複跟 AI 講代碼風格、commit 風格、做事流程**。
把你家的「規矩」(house rules) 設定一次，每個專案自動套用，維持穩定品質。

靈感來自 George Xing 的 *How I build with AI as a 1-person company*（brainstorm → plan →
execute → review 四段式工作流 + 雙模型互審），再加上一個明確的 **CEO 統籌角色**。

---

## 它是什麼

一個由四個角色組成的團隊，你只跟 **CEO** 對話，其餘角色由 CEO 調度：

| 角色 | 用誰 | 職責 |
|------|------|------|
| **CEO**（`/ceo`） | Claude（大腦可換，預設馬斯克思維） | 跟你腦力激盪、產出 PRD/SDD/Plan、派活、彙整回報。你唯一直接對話的對象。 |
| **Coder**（`/coder`） | Claude | 照 SDD/Plan 寫代碼、依風格 commit。 |
| **Reviewer**（`/reviewer`） | **Codex（不同模型）** | 設計審查 + 代碼審查，出結構化報告，loop 到通過。 |
| **Tester**（`/tester`） | Claude + MCP | 跑真實使用者場景測試 / 查證。 |

**雙模型互審**：Claude 寫、Codex 審。不同模型盲點不同，審得更嚴。

非代碼任務（寫作 / 研究）時，CEO 會自動把角色換成 **Drafter / Editor / Fact-checker**，同一套流程不變。

---

## 工作流程

```
你 ▶ CEO ─腦力激盪→ prd.md
         ─設計→     sdd.md ──(Reviewer 設計審查)──┐ 通過才往下
         ─拆解→     plan.md                       │
                       ▼                           │
                  Coder ─寫+commit→ 代碼            │
                       ▼                           │
                  Reviewer ─代碼審查→ reviews/  ─(loop 修到過)
                       ▼
                  Tester ─場景測試→ tests/
                       ▼
                  CEO 彙整回報你
```

角色之間透過 `.ai-team/` 資料夾的檔案傳遞訊息（可追溯、跨工具）。

---

## 安裝

```bash
npx skills add <你的帳號>/houserules-skills
```

需求：
- **Claude Code**（CEO / Coder / Tester）
- **Codex CLI** ≥ 0.124（Reviewer）— 終端可執行 `codex`
- （選配）**gemini-cli**（研究 / 查證任務）
- （選配）Playwright-MCP / XcodeBuildMCP（Tester 跑 web / iOS 測試）

---

## 快速開始

1. 在你的專案目錄打開 Claude Code。
2. 輸入 `/ceo`，描述你想做的事。
3. 第一次會跑一段 **init 問答**，自動在 `.ai-team/` 生成你的設定檔（風格、commit、CEO 大腦）。
4. 之後 CEO 會帶著整個團隊跑完 brainstorm → 設計 → 寫 → 審 → 測。

---

## 客製化（兩層設計）

skill 本體（出廠預設，不要改）＋ 你的專案層設定（`.ai-team/`，隨專案走、可覆蓋）：

| 檔案 | 作用 |
|------|------|
| `.ai-team/config.md` | 總開關：啟用哪些角色、模型、任務型態 |
| `.ai-team/style.md` | 代碼風格 |
| `.ai-team/commit.md` | commit 訊息風格 |
| `.ai-team/ceo-brain.md` | CEO 思維（預設馬斯克，可換） |

詳見 [docs/customization.md](docs/customization.md)。

## 換掉 CEO 大腦（接 nuwa）

預設 CEO 用馬斯克的第一性原理思維。想換成別人，用
[nuwa-skill](https://github.com/alchaincyf/nuwa-skill) 蒸餾出該人物的認知框架，貼進
`.ai-team/ceo-brain.md` 即可。詳見 [docs/nuwa-integration.md](docs/nuwa-integration.md)。

---

## 授權

MIT
