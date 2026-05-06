# SPP Foundry Labs / Works Content Strategy

## 1. 核心決策

SPP Foundry 主站的內容結構分為 `/labs/` 與 `/works/`，兩者應該有清楚分工，避免未來 AICert、Flow Booking、Bitemap、BOOM 等專案各自定義混亂。

- `/labs/`
  - MVP
  - 小工具
  - 互動 demo
  - 可操作產品原型
  - 讓使用者直接體驗產品流程

- `/works/`
  - 作品集
  - case study
  - 對外展示「我做過什麼」
  - 產品說明頁
  - SEO/GEO 主內容頁
  - 商業轉換與信任建立頁

核心分工：

- Labs 負責「體驗」。
- Works 負責「說明、說服、被搜尋、被引用」。

## 2. Labs 的角色

`/labs/` 是 SPP Foundry 的 MVP showcase 區域。它的主要任務不是承載大量文字，而是讓使用者直接操作、感受產品流程，快速理解這個實驗或工具能做什麼。

適合放在 Labs 的專案：

- AICert 這類可互動 AI 學習工具。
- Flow Booking 這類可實際操作的預約系統 demo。
- BOOM 這類生成器或互動工具。
- Bitemap 這類小型 AI / web utility。

Labs 頁面原則：

- 以可操作體驗為主。
- 保持簡潔。
- 不塞大量銷售文案。
- 不讓 SEO 文字干擾使用者操作。
- 可以保留極短產品識別、簡短說明、必要導覽。

## 3. Works 的角色

`/works/` 是 SPP Foundry 的案例頁與商業展示區域。它適合用較完整的敘事，說明一個產品或專案的背景、問題、解法、技術選型、成果與後續方向。

適合放在 Works 的內容：

- Flow Booking case study。
- AICert case study。
- Bitemap / BOOM 產品故事。
- 技術架構說明。
- 問題 → 解法 → 成果。
- Demo 入口。
- FAQ。
- SEO/GEO 長內容。
- 未來服務包裝與接案信任建立。

Works 頁面原則：

- 可以承載較完整的產品說明。
- 可以放案例故事與截圖。
- 可以放技術選型與系統架構。
- 可以放 FAQ 與長尾關鍵字內容。
- 可以作為 Google / AI 搜尋引擎理解 SPP Foundry 能力的主內容頁。

## 4. Labs / Works 對應表

| Project | Labs URL | Works URL | Labs purpose | Works purpose |
|---|---|---|---|---|
| AICert | `/labs/aicert/` | `/works/aicert/` | 互動學習 / 證照練習 MVP | AI 學習產品案例與內容策略 |
| Flow Booking | `/labs/flow-booking/` | `/works/flow-booking/` | 預約系統 live demo / MVP | 一人商家預約系統 case study |
| BOOM | TBD（`/labs` 或 subdomain 待定） | `/works/boom/` | 互動祝福生成器 | 節慶生成器產品案例 |
| Bitemap | TBD（`/labs` 或 subdomain 待定） | `/works/bitemap/` | 小工具 / demo | AI utility / map-style product case |

尚未決定的 URL 以 TBD 標記，不假裝已完成。

## 5. Flow Booking 的特殊決策

Flow Booking 的頁面分工應明確切開：

- `/labs/flow-booking/` 保持為 demo / 預約體驗頁。
- 不把大量 SEO/GEO 長文案塞進預約頁。
- Labs 頁只做輕量 SEO metadata、OG image、必要產品識別。
- 完整產品說明、FAQ、案例故事、技術架構，未來放在 `/works/flow-booking/`。
- 這個決策來自 Flow Booking SEO/GEO Phase 2 規劃。

這樣可以保留朋友 demo 與實際預約體驗的簡潔度，同時讓未來 Works 頁承擔搜尋、說明與商業信任建立。

## 6. AICert 可沿用的邏輯

AICert 也可以沿用 Labs / Works 分工：

- `/labs/aicert/` 保持可互動的 AI 學習 / 證照練習工具。
- 未來 `/works/aicert/` 可放產品故事、學習設計邏輯、技術架構、內容策略、成效與截圖。
- 不需要把大量說明塞進工具頁本身。

這個模式可以讓 AICert 的工具體驗維持集中，也讓完整產品價值與 SEO/GEO 內容有更合適的位置。

## 7. SEO/GEO 原則

### Labs

- 可被搜尋，但不是主要長文內容承載區。
- 優先保留互動體驗。
- SEO 以 metadata、OG image、簡短說明為主。
- 內容密度應控制在不干擾操作的範圍內。

### Works

- 是 SEO/GEO 主力頁。
- 可放定義型內容、FAQ、案例、技術說明、長尾關鍵字。
- 讓 ChatGPT、Perplexity、Google AI Overviews 更容易引用 SPP Foundry 的作品與能力。
- 可以承載商業轉換、信任建立與作品集展示。

## 8. 後續待辦

- 建立 `/works/` 主入口頁。
- 建立 `/works/flow-booking/` 第一個 case study。
- 建立 `/works/aicert/` case study。
- 檢查 `/labs/` 現有作品入口。
- 統一 Labs / Works 的內部連結策略。
- 決定 BOOM / Bitemap 是否保留 subdomain 或同步建立 Works 頁。
- 未來把這份策略同步回各專案文件。
