# 換掉 CEO 大腦（接 nuwa-skill）

CEO 的思維由 `.ai-team/ceo-brain.md` 決定，預設是 **Elon Musk 第一性原理**。
想讓 CEO 用另一位人物的決策框架跟你腦力激盪，用
[nuwa-skill](https://github.com/alchaincyf/nuwa-skill) 蒸餾出那個人的「認知作業系統」，
覆蓋這個檔案即可。我們採**鬆耦合**：CEO 不依賴 nuwa 也能跑（有預設大腦），有就增強。

## 步驟

1. 安裝 nuwa：
   ```bash
   npx skills add alchaincyf/nuwa-skill
   ```
2. 蒸餾你想要的人物（nuwa 會跑多路研究並生成一份 SKILL.md 格式的認知框架）：
   ```
   蒸餾一個 <人物名>
   ```
3. 把 nuwa 產出的框架內容貼進 `.ai-team/ceo-brain.md`，**整檔覆蓋**。
   建議保留我們模板末尾的兩段：
   - 「用在這個 CEO 角色上（How to apply）」——把該人物的思維對應到 PRD/SDD/派活/品質關卡。
   - 「誠實的限制」——提醒這是公開資訊重建的近似，且該風格不適用所有情境。
4. 下次 `/ceo` 就會用新大腦。

## 注意
- `ceo-brain.md` 是**視角 / 決策框架**，不是角色扮演——目的是換一種「怎麼想問題」的方式，
  不是模仿語氣而已。
- 不同人物適合不同任務：偏執行/硬體用馬斯克式刪減；偏產品體驗、偏研究嚴謹度時可換更合適
  的框架。可為不同專案放不同的 `ceo-brain.md`。
- 想保留多顆大腦：在 `.ai-team/brains/` 放多份（如 `musk.md`、`jobs.md`），要用哪顆就
  複製成 `ceo-brain.md`。
