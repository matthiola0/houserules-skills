# Commit 訊息風格（house rules）

> Coder 每次 commit 都遵守。預設已套用「乾淨、無 AI 署名」風格，符合多數人習慣。

## 硬規則（不可違反）
- **絕不**加 `Co-Authored-By` 或任何 AI / Claude / Codex 署名與工具簽名。
- 不加表情符號、不加廣告行（如「Generated with ...」）。

## 格式
- 主旨：**祈使句（imperative）**、≤ 50 字、句首大寫、句尾不加句號。
  - 好：`Add retry to upload client`
  - 壞：`added retry`、`fixes stuff`
- 主旨後空一行，再寫 body（非必要可省）。body 說明 **what / why**，不是逐行複述 diff。
- 一個 commit 一件事；不要把無關變更混在一起。

## 範例
```
Add retry with backoff to upload client

Uploads failed intermittently on flaky networks. Retry up to 3 times
with exponential backoff so transient 5xx no longer surface to users.
```

## 選配慣例（init 可開啟）
- Conventional Commits 前綴（`feat:` / `fix:` / `refactor:` ...）：<on/off>
