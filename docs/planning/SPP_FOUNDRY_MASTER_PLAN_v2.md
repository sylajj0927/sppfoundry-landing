# SPP Foundry Master Plan v2

Site Strategy & Homepage Master Plan · 2026

本文件是 SPP Foundry 主站的主控文件。首頁設計、資訊架構、視覺方向、Phase 1 狀態與後續實作，皆以本文件為準。`SPP_FOUNDRY_CONTENT_STRATEGY_V2.md` 只負責補充 Labs / Works 的內容分工。

---

## 1. 品牌定位

### 品牌名稱

SPP Foundry

### 一句話定位

AI × Vibe Coding 產品陪跑實驗室，陪小型商家、創作者與個人品牌，把想法做成第一個可用版本。

### 首頁核心精神

AI × Vibe Coding 產品陪跑實驗室  
從產品發想到落地，陪你做出第一個可用版本。

首頁不是完整說明頁，也不是服務型錄，而是品牌入口與分流頁：

- 想看做過哪些 AI 小產品 / 實驗作品 → 看 Labs。
- 想了解如何把想法落成第一版 → 看產品陪跑。
- 想討論自己的想法 → 到底部 Contact「和我聊聊」。

---

## 2. 首頁角色

首頁 `/` 的任務是：

- 快速傳遞 SPP Foundry 是什麼。
- 讓訪客理解「AI 小產品」「產品陪跑」「自動化」三個方向。
- 導流到 Labs、產品陪跑、Contact。
- 保持輕量，不承載完整產品說明、服務說明或 SEO 長文。

首頁應避免：

- 像工程資訊頁、SaaS 功能頁、dashboard template。
- 像 Claude Code workspace 或大面積 AI workspace 風格。
- 像厚重 serif 大字報。
- 把 BOOM、BiteMap、Resize Helper 等小工具硬包裝成完整 MVP。
- 把 n8n / LINE Bot 技術細節塞進首頁。

---

## 3. 內容架構

| 區域 | 路徑 | 角色 |
|---|---|---|
| 首頁 | `/` | 品牌入口 + 快速理解 + 分流 |
| Labs | 依現有與未來入口決定 | AI 小產品與實驗作品，可直接體驗 |
| Works | 未來建立 | 說明、說服、被搜尋、被引用的案例內容 |

Labs / Works 詳細分工以 `SPP_FOUNDRY_CONTENT_STRATEGY_V2.md` 為準。

---

## 4. 首頁錨點結構

Phase 1 首頁使用單頁錨點結構，不新增子頁面：

`/ → #hero → #what-i-build → #labs → #how-it-works → #automation → #services → #about → #contact`

注意：舊的 `#featured-work` 已改為 `#how-it-works`。語意從「精選作品」改成「我如何陪你把想法做成第一版可用產品」。

### 4.1 Hero

目的：讓訪客在第一屏快速理解品牌精神與下一步。

文案方向：

- 小眉標：AI × Vibe Coding 產品陪跑實驗室
- 主標：把想法，整理成可以開始的版本。
- 副標：從產品發想到落地，陪你做出第一個可用版本。
- 補充：把模糊的點子，做成可以體驗、展示與驗證的第一版。

Hero CTA 只保留兩個：

- 看 AI 小產品 → `#labs`
- 了解產品陪跑 → `#how-it-works`

「和我聊聊」不放在 Hero CTA。它只放在導覽的「聯絡」與底部 Contact 區塊。

### 4.2 What I Build

主標方向：

把模糊的點子，整理成可以被打開的入口。

四個能力方向，每項只保留一句：

- AI 小工具 / MVP：把生成器、學習工具或查詢工具做成可體驗版本。
- 一人商家流程工具：整理預約、表單、通知與紀錄流程。
- n8n / LINE Bot 自動化：把重複資訊整理成推播、摘要或紀錄。
- 產品企劃與陪跑：把需求、Sitemap 與 MVP 範圍收斂清楚。

### 4.3 Labs

首頁 Labs 用語：

AI 小產品與實驗作品

Intro 方向：

從真實需求出發，做成可以直接打開使用的小工具、MVP 與互動作品。

目前首頁展示：

- Flow Booking：一人商家極簡預約 MVP。
- AICert / AI 魔法詞典：AI 學習與證照練習工具。
- BOOM：2026 新年祝福產生器。
- BiteMap Taipei：主題式美食地圖小工具。

分類原則：

- Flow Booking、AICert 可以視為較完整的 MVP。
- BOOM、BiteMap、未來 Resize Helper 屬於 AI 小產品 / 實驗作品，不硬說成完整 MVP。

### 4.4 How It Works / 產品陪跑

Section id：`#how-it-works`

目的：說明 SPP Foundry 如何陪使用者把想法做成第一版可用產品。這一段可用 Flow Booking 作為代表例子，但不寫成完整 case study。

語意方向：

- 從模糊需求開始。
- 收斂成可操作流程。
- 做出第一版可體驗 MVP。
- 用 Flow Booking 證明這套方式。

CTA：

- 體驗 Flow Booking → `/labs/flow-booking/`
- 閱讀案例 Coming Soon：不可點擊，不假裝未完成頁面已存在。

### 4.5 Automation

首頁只放摘要，不做完整流程說明。

主標：

把重複的資訊流，整理成溫和但可靠的自動化。

流程最多三步：

收集資訊 → AI 整理 → LINE / Sheet / 知識庫

n8n / LINE Bot 類無法公開體驗者不開 Labs，未來放 Works 做案例。

### 4.6 Services

主標：

合作不是先買一套服務，而是先把問題說清楚。

三個方向，每項最多一句：

- AI MVP 陪跑：從想法整理到第一版 demo。
- 小型工具 / Landing Page：做出可以被體驗的入口與流程。
- n8n / LINE Bot 自動化：整理推播、紀錄與日常資訊流。

不放價格表，不做服務型錄。

### 4.7 About

保持短，2–3 行即可。

方向：

SPP Foundry 是我把 AI、Vibe Coding 與自動化實驗整理成作品、案例與服務的地方。第一版產品不需要很大，先能使用、能理解、能回饋。

### 4.8 Contact

底部 Contact 是主要「和我聊聊」位置。

標題：

有一個想法，先聊聊。

內文方向：

不用一開始就準備完整規格。先把問題、對象與使用情境說清楚，再整理成可以開始的版本。

CTA：

- 和我聊聊 → 使用既有首頁 email。
- 查看作品 → `#labs`，只能作為次要連結。

---

## 5. 導覽策略

桌機中文導覽建議：

作品 / 陪跑 / 合作 / 關於 / 聯絡

手機版可精簡為：

作品 / 陪跑 / 聯絡

手機導覽不需要完整顯示所有 nav items，避免擠成一排小字。

---

## 6. 視覺設計規範

### 整體方向

- 更乾淨、更白、更少字。
- 更像 soft editorial personal brand 入口頁。
- 快速掃描，不像工程資訊頁或長篇企劃書。
- 不使用 stock photo、科技感 3D 圖、紫色漸層。
- 不使用大面積米黃背景，不做 Claude Code workspace 感。

### 色彩

- 主背景接近純白：`#FFFFFF`、`#FCFBF8`、`#FAFAF7`。
- 局部點綴可用霧綠、淡粉米、陶土色。
- 邊框與分隔線使用低對比暖灰。
- 避免整頁 Oatmeal / Beige 佔滿視覺。

### 字體

- 中文優先使用 system sans、PingFang TC、Noto Sans TC。
- 不要求 DM Serif / DM Sans。
- 可局部保留少量 serif 作為品牌點綴，但大標題不要厚重 serif 大字報感。
- 手機 h1 約 34–40px，不超過 42px。
- 手機 h2 約 28–34px。

### 視覺符號

- 可使用 inline SVG 細線 icon，不引入外部 icon library。
- Hero 右側若有符號，應具備 SPP Foundry 意義，例如「想法 → 流程 → 第一版」。
- 手機版 Hero 視覺符號可縮小、移到 CTA 後方，或直接隱藏，以確保首屏完整。

---

## 7. Mobile-first 原則

手機版不是桌機版縮小，而是首頁入口的優先體驗。

手機版需符合：

- 第一屏盡量完整呈現 header、眉標、主標、副標、兩個 CTA。
- 導覽精簡，不完整顯示所有項目。
- Hero 右側視覺不能切斷首屏節奏。
- section 間距更緊湊但不擠。
- What I Build、Labs、How It Works、Automation、Services 都應可快速掃描。
- Flow Booking 主卡手機版不可過高。
- CTA 不撐滿成表單感，保持品牌入口語氣。
- About / Contact 收尾俐落，不用大段引用式文字。

---

## 8. SEO / GEO 原則

首頁：

- 輕量 SEO。
- 以 title、description、OG、basic Organization JSON-LD 為主。
- 不新增 FAQ schema。
- 不塞長尾 SEO 文章。

Labs：

- 以可操作體驗為主。
- 可做輕量 metadata / OG image。

Works：

- 未來承載 case study、FAQ、技術說明、SEO / GEO 長內容。

---

## 9. 實作邊界

可以做：

- 修改根目錄首頁 `index.html`。
- 保持純靜態 HTML/CSS。
- 調整首頁視覺、文案、錨點、mobile refinement。

不要做：

- 不改 `/labs/flow-booking/**` 既有產品邏輯。
- 不改 `/labs/aicert/**` 既有產品邏輯。
- 不新增 Vite / React / Tailwind 或 JS build pipeline。
- 不新增 `/works/`、`/services/`、`/articles/` 頁面。
- 不新增 `/labs/` 總覽頁，除非未來另行決策。
- 不把 Coming Soon 變成可點擊假連結。
- 不新增未確認價格表。
- 不 build、不 deploy、不 commit，除非使用者明確要求。

---

## 10. Phase 狀態

### Phase 1.9 目前狀態

- 首頁 `index.html` 已完成 Phase 1.9 refinement。
- 已完成純靜態首頁，不導入 framework。
- 已完成首頁入口頁定位、Hero 兩個 CTA、`#how-it-works`、AI 小產品語言、mobile refinement。
- 尚未 build。
- 尚未 deploy。
- 尚未 commit。

### Phase 2

- 建立 Works 入口與第一批 case study。
- 優先處理 Flow Booking case study。
- 再處理 AICert、BOOM、BiteMap、n8n / LINE Bot 類案例。

### Phase 3

- 建立 Services 獨立頁。
- 建立 Articles / SEO 長內容。
- 補 SEO / GEO 長內容與 FAQ。

© SPP Foundry · hello@sppfoundry.co · v2.0 · 2026
