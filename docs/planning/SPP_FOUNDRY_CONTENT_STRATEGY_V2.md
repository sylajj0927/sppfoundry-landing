# SPP Foundry Labs / Works Content Strategy V2

本文件只負責 SPP Foundry 的 Labs / Works 分工策略。首頁資訊架構、Hero、視覺規範、mobile-first 原則與 Phase 狀態，以 `SPP_FOUNDRY_MASTER_PLAN_v2.md` 為準。

---

## 1. 核心分工

SPP Foundry 主站分為三個內容層：

- `/` 首頁：品牌入口 + 快速理解 + 分流。
- Labs：AI 小產品與實驗作品，讓使用者直接體驗。
- Works：案例說明、商業說服、SEO / GEO 主內容。

核心原則：

- 首頁負責「快速理解與導流」。
- Labs 負責「體驗」。
- Works 負責「說明、說服、被搜尋、被引用」。

首頁目前以錨點導流為主，其中產品陪跑區塊使用 `#how-it-works`，不是舊的 `#featured-work`。

---

## 2. Labs 的角色

Labs 是「AI 小產品與實驗作品」區域，不只放完整 MVP，也可以放較小的互動工具、生成器、資料工具與可操作 demo。

適合放在 Labs 的內容：

- 可直接打開使用。
- 可快速理解產品概念。
- 不需要大量背景說明就能體驗。
- 不涉及私人資料、後台權限或個人化帳號綁定。

Labs 頁面原則：

- 以可操作體驗為主。
- 保持簡潔。
- 不塞大量銷售文案。
- 不讓 SEO 長文干擾使用者操作。
- 可保留輕量 metadata、OG image、必要產品識別。

分類語言：

- Flow Booking、AICert 可視為較完整的 MVP。
- BOOM、BiteMap、未來 Resize Helper 屬於 AI 小產品 / 實驗作品，不硬說成完整 MVP。

### Labs 卡片視覺層級決策（2026-05-07）

- Flow Booking 為首張大卡，視覺優先性已足夠，不需額外 Featured Lab 標籤。
- 不使用 Featured Lab 這類英文附加標籤，避免手機版視線干擾，也避免未來產品增加後需要重新排序 featured 的維護問題。
- 站內連結箭頭使用 `→`，外部連結箭頭使用 `↗`（文字符號，不允許 emoji 渲染）。
- Labs 卡片這輪只做資訊層級微修，整體視覺重設計暫緩，待 Works 第一批 case study 確立後再評估。

---

## 3. Works 的角色

Works 是案例頁與商業展示區域，用較完整的敘事說明產品背景、問題、解法、流程設計、成果與後續方向。

適合放在 Works 的內容：

- Flow Booking case study。
- AICert case study。
- BOOM / BiteMap 產品故事。
- Resize Helper 等小工具背後的產品判斷與設計邏輯。
- n8n / LINE Bot 自動化案例。
- 問題 → 解法 → 成果。
- 技術選型與系統架構。
- FAQ 與長尾關鍵字內容。
- 商業轉換與接案信任建立內容。

Works 頁面原則：

- 可以承載較完整的產品說明。
- 可以放案例故事、截圖、技術說明、FAQ。
- 是 Google、ChatGPT、Perplexity、Google AI Overviews 理解 SPP Foundry 能力的主內容層。
- 不干擾 Labs 的操作體驗。

---

## 4. Labs / Works 對應表

| Project | Labs URL / 入口狀態 | Works URL / 狀態 | Labs 用途 | Works 用途 |
|---|---|---|---|---|
| Flow Booking | `/labs/flow-booking/` | 未來 `/works/flow-booking/` | 一人商家極簡預約 MVP / live demo | 一人商家預約流程 case study |
| AICert | `/labs/aicert/` | 未來 `/works/aicert/` | AI 學習與證照練習工具 / MVP | AI 學習產品案例與內容策略 |
| BOOM | `https://boom.sppfoundry.co` 或 TBD | 未來 Works 內容 TBD | 2026 新年祝福產生器 / 小產品 | 節慶生成器產品故事 |
| BiteMap | `https://bitemap.sppfoundry.co` 或 TBD | 未來 Works 內容 TBD | 主題式美食地圖小工具 | AI utility / map-style case |
| Resize Helper | 未上線 / future | 未來 Works 內容 TBD | 圖片 resize 類小工具候選 | 小工具設計邏輯與使用情境 |
| 每日唸經記錄 | 不開 Labs | 未來 Works 內容 TBD | — | n8n 自動化紀錄案例 |
| Sylvia AI 小助理 | 不開 Labs | 未來 Works 內容 TBD | — | LINE Bot AI 助理案例 |

注意：

- 不假裝 BOOM / BiteMap 已有 `/labs/boom/` 或 `/labs/bitemap/`。
- Resize Helper 是未上線 / future 候選，不建立不存在的 URL。
- Works URL 若尚未建立，以未來內容 TBD 標記，不把未完成頁面當成已存在。

---

## 5. 自動化產品歸類

n8n / LINE Bot 類產品常涉及私人資料、後台流程、LINE 帳號、Google Sheet 或非公開 webhook，因此原則上不開 Labs。

例如：

- 每日唸經記錄。
- Sylvia AI 小助理。
- AI 新聞 / AI 神器 / 經濟部快訊推播。
- 今日待辦、知識庫、旅遊住宿等自動化助理。

這類內容應放 Works，說明：

- 問題背景。
- 自動化流程設計。
- 資料來源與輸出位置。
- AI 摘要 / 分類 / 推播邏輯。
- 成效或截圖。

---

## 6. Flow Booking 分工

Flow Booking 的分工需清楚切開：

- `/labs/flow-booking/` 保持 demo / 預約體驗頁。
- Labs 頁不塞大量 SEO / GEO 長文。
- 完整產品說明、FAQ、案例故事、技術架構，未來放 Works。
- 首頁 `#how-it-works` 可引用 Flow Booking 作為產品陪跑代表例，但不寫成完整 case study。

---

## 7. AICert 分工

AICert 沿用 Labs / Works 分工：

- `/labs/aicert/` 保持可互動的 AI 學習 / 證照練習工具。
- 未來 Works 可放產品故事、學習設計邏輯、技術架構、內容策略、成效與截圖。
- 不需要把大量說明塞進工具頁本身。

---

## 8. SEO / GEO 原則

首頁：

- 輕量 SEO。
- 以 metadata、OG image、品牌定位句為主。
- 不做長尾主力頁。

Labs：

- 可被搜尋，但不是主要長文內容承載區。
- 優先保留互動體驗。
- SEO 以 metadata、OG image、簡短說明為主。

Works：

- 是 SEO / GEO 主力頁。
- 可放定義型內容、FAQ、案例、技術說明、長尾關鍵字。
- 可作為 Google / AI 搜尋引擎理解 SPP Foundry 能力的主內容頁。

---

## 9. 後續待辦

- [x] 首頁 `/` 完成 Phase 1.9 refinement。
- [x] Labs 卡片資訊層級微修：移除 Featured Lab、箭頭標準化（2026-05-07）。
- [ ] 建立 Works 入口與第一批 case study。
- [ ] 建立 Flow Booking case study。
- [ ] 建立 AICert case study。
- [ ] 規劃 BOOM / BiteMap 是否維持 subdomain，或未來同步整理 Works 內容。
- [ ] 評估 Resize Helper 是否作為未來 Labs 小工具。
- [ ] 建立 n8n / LINE Bot 類 Works 案例。
- [ ] 統一 Labs / Works 的內部連結策略。
