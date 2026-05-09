# SPP Foundry Homepage Visual Refinement Plan v1

節奏線系統 v1：保守精修版

> 本文件是 SPP Foundry 主站首頁 Phase 1.9 之後的第一份視覺精修計畫。
> 本輪採用方案 A（保守精修版），目標是建立第一個跨 section 的視覺記憶單元，不動既有元件結構與文案。
> 本文件不取代 `SPP_FOUNDRY_MASTER_PLAN_v2.md` 或 `SPP_FOUNDRY_CONTENT_STRATEGY_V2.md`，僅作為一次性視覺精修的執行依據。

---

## 1. 本輪目標

1. 在首頁主要 section label 上方建立一條暖橘短橫線，形成「章節記號」式的視覺單元。
2. 微調 section-intro 桌機留白，讓標題塊與內容塊有更清楚的獨立性。
3. 微調 Services 段的 row 節奏，讓三條 row 之間更有呼吸感、暖橘短線更明確。
4. 不動 Hero / What I Build / Labs / How It Works / Automation / About / Contact 的既有結構與文案。

本輪不引入：

- 新顏色
- 新 SVG / icon
- 新動畫
- 藍色 CTA
- 卡片元件改動
- HTML 結構改動

---

## 2. 設計判斷

### 2.1 為什麼是「短橫線 + section-intro spacing + Services row 節奏」三件事

- 三件事都是純 CSS 變更，HTML 不動。
- 三件事都集中在「typography 與留白」層級，不涉及卡片、icon、SVG。
- 三件事可以一次寫完，符合每天 1–2 小時推進節奏。
- 三件事完成後，整站會出現第一個跨 section 重複的視覺單元（短橫線），這是品牌一致性最便宜的提升方式。
- Services 段是「合作入口」，這段先成熟比 Hero 先成熟對接案信任建立更有用。

### 2.2 為什麼不動 Hero / Labs / How It Works / Automation

- Hero 上輪試過紅藍曲線並回退，重做容易循環踩坑。
- Labs 2026-05-07 剛完成 Featured Lab / 箭頭 / kicker 微修，本輪再動會浪費剛收斂好的層級。
- How It Works 剛調過文案、節點、CSS 直線。再動容易破壞剛收斂的內容。
- Automation 牽涉橫向 flow 與直向 mobile flow 雙 breakpoint，動了容易壞手機版。

### 2.3 為什麼不引入新色

- `--clay: #a9634f` 已經是一個有暖度、有編輯感的紅橘色，比設計參考的純紅 `#d63b3b` 更符合 SPP Foundry 氣質。
- 本輪的核心是把現有 clay「升格」為節奏色，而不是引入第二種紅。
- 引入新色會連帶要重新評估整套 button / kicker / arrow / card-action 的色彩語言，超出本輪邊界。

---

## 3. 實作範圍盤點

### 3.1 `.kicker` 出現位置

`.kicker` 在 `index.html` 共出現 6 次，全部位於主要 section label：

| 行號 | section | 內容 |
|---|---|---|
| 1336 | `#what-i-build` | What I Build |
| 1383 | `#labs` | Labs |
| 1441 | `#how-it-works` | How It Works |
| 1468 | `#automation` | Automation |
| 1494 | `#services` | Services |
| 1525 | `#contact` | Contact |

全部 6 處都包在 `<div class="section-intro">` 內，結構一致：

```
<section>
  <div class="section-intro">
    <div>
      <p class="kicker">XXX</p>
      <h2>...</h2>
    </div>
    <p>...（部分 section 有副文）</p>
  </div>
</section>
```

注意：

- Hero 不使用 `.kicker`，使用的是 `.eyebrow`（line 1303），動 `.kicker` 不會影響 Hero 第一屏。
- About 不使用 `.section-intro`，使用 `.section-rule` + `.quote-block`，自然不會有短橫線，符合 About 是引言段、不需要章節記號的語意。

### 3.2 Selector 選擇

採用：`.section-intro .kicker::before`

理由：

- 不採用裸 `.kicker::before`：未來若 `.kicker` 被套到 section 以外的位置（如 Works case study 內頁的 metadata label），會自動長線，綁太死。
- 不採用 `.section-intro::before`：`.section-intro` 是 `display: grid` 兩欄佈局，加 `::before` 會被當成 grid item 佔掉一格，破壞兩欄結構。
- `.section-intro .kicker::before` 把短橫線明確限定在「section-intro 內的 kicker」上方，符合「現在乾淨、未來不誤觸發」原則。

---

## 4. 變更清單

只動下列 4 個 CSS selector，HTML 完全不動。

### 4.1 新增：`.section-intro .kicker::before`

桌機短橫線本體。

| 屬性 | 值 |
|---|---|
| content | `""` |
| display | `block` |
| width | `40px` |
| height | `1px` |
| background | `var(--clay)` |
| opacity | `0.7` |
| margin-bottom | `16px` |

### 4.2 修改：`.section-intro`（既有，line 336–342）

桌機 `margin-bottom: 38px` → `56px`。
不動 `grid-template-columns`、`gap`、`align-items`。

### 4.3 修改：`.service-row`（既有，line 781–789）

桌機 `padding: 28px 0` → `32px 0`。
不動 `grid-template-columns`、`gap`、`align-items`、`border-bottom`、`::before` 短線。

### 4.4 修改：`.service-row::before`（既有，line 791–799）

`background: rgba(173, 101, 78, 0.42)` → `rgba(173, 101, 78, 0.55)`。
不動 `width`、`height`、`position`。

---

## 5. 手機版處理

### 5.1 短橫線 mobile override

新增：

```
@media (max-width: 640px) {
  .section-intro .kicker::before {
    width: 28px;
    margin-bottom: 12px;
  }
}
```

放在既有 640px override 區段（line 937 開始）內，跟既有 `.kicker` mobile 規則（line 1002–1007）放在一起。

920px 不單獨 override，桌機 40px 線在 920px 區間看起來合理。

### 5.2 section-intro spacing：維持現況

不動 mobile `.section-intro` margin-bottom。既有 mobile override（line 1050–1053）已將 mobile margin-bottom 收到 24px，是上輪剛調好的，不要動。

桌機改成 56px 不會傳染到 mobile，因為 mobile 有自己的 override 蓋掉。**這是本輪最低風險的關鍵點。**

### 5.3 service-row padding：跟著桌機

桌機 32px 0 在 mobile 會生效，三條 row 在手機上會稍微更寬鬆，這是想要的。

不預先寫 mobile override，避免未測試先優化。實測後若覺得 mobile 32px 過空，再加 override 收回 28px。

### 5.4 Horizontal overflow 風險評估

| 變更 | overflow 風險 |
|---|---|
| `.section-intro .kicker::before` 短橫線（40px / 28px） | 無。固定寬度遠小於容器。 |
| `.section-intro margin-bottom` 56px | 無。垂直方向變更。 |
| `.service-row padding` 32px 0 | 無。垂直方向變更。 |
| `.service-row::before` 顏色加深 | 無。視覺變更，不改幾何。 |

唯一需要實測確認的點：

- 桌機下，`.section-intro .kicker::before` 短橫線是否準確停在 kicker 正上方，而不是被推到 section-intro 容器最頂、或跑到 grid 第二欄上方。
- 預期：因為 `::before` 綁在 `.kicker` 元素上，會跟著第一欄 grid item 走。第一次實作時建議在 DevTools 直接試一次確認。

---

## 6. 預期效果

完成後可觀察到：

- 整站每個主要 section 開頭出現共用的暖橘短橫線，建立第一個品牌記憶點。
- Services 段從「最平的一段」升級成「最有書頁感的一段」，反襯出整頁節奏。
- 短橫線桌機 40px、手機 28px，視覺上像「翻頁的章節記號」，不像分隔線。
- 不動任何卡片、不動任何 icon、不動任何文案。
- 手機版穩定不變。

---

## 7. 不動範圍（明確邊界）

本輪不動：

- Hero 全部（`hero-card`、`hero-symbol`、SVG、`eyebrow`、`h1`、CTA）
- What I Build（`build-list`、`build-item`、icon、grid、文案）
- Labs（`lab-feature`、`lab-stack`、`lab-link`、`mini-tags`、`arrow`、`card-action`）
- How It Works（`how-case`、`case-notes`、`case-note`、`note-number`、`case-label`、`.case-notes::before`）
- Automation（`automation-wrap`、`flow`、`flow-step`、icon）
- About（`section-rule`、`quote-block`）
- Contact（`contact-card`、`actions`、CTA）
- Nav 與 Footer
- Button 系統（`.button.primary` / `.secondary` / `.text` / `.disabled`）
- `:root` color tokens
- 920px 與 640px 既有 mobile override（除 5.1 新增 `.kicker::before` mobile override 外）
- HTML 結構

不引入：

- 新色
- 新 SVG
- 新 icon
- 新動畫
- 新 class
- 新 component

---

## 8. 風險與回退方案

### 8.1 風險

| 風險 | 嚴重度 | 處理 |
|---|---|---|
| 短橫線位置跑到 grid 第二欄上方 | 中 | DevTools 先試，必要時改用 `.section-intro > div > .kicker::before` 限定第一欄 |
| 桌機 56px margin-bottom 看起來太空 | 低 | 收到 48px |
| Mobile service-row 32px padding 太空 | 低 | 加 mobile override 收回 28px |
| 短橫線 opacity 0.7 太重 | 低 | 收到 0.55–0.6 |
| `::before` 影響既有 kicker 上方 padding 計算 | 低 | 用 `display: block` + `margin-bottom`，不用 `position: absolute`，不影響流式排版 |

### 8.2 回退方案

完整回退指令：

- 移除新增的 `.section-intro .kicker::before` 規則
- 移除新增的 `@media (max-width: 640px) .section-intro .kicker::before` 規則
- `.section-intro` margin-bottom 改回 38px
- `.service-row` padding 改回 28px 0
- `.service-row::before` background 改回 `rgba(173, 101, 78, 0.42)`

回退影響範圍：純 CSS，無 HTML 變更，無 build pipeline 變更。

---

## 9. 預設值

如果沒有額外指定，本輪採用：

- 短橫線桌機寬度：40px
- 短橫線桌機 opacity：0.7
- 短橫線桌機 margin-bottom：16px
- 短橫線手機寬度：28px
- 短橫線手機 margin-bottom：12px
- section-intro 桌機 margin-bottom：56px
- service-row 桌機 padding：32px 0
- service-row::before 顏色 alpha：0.55

三個關鍵決策可調整：

- opacity 0.7（替代值 0.55–0.6 更含蓄）
- section-intro 桌機 margin-bottom 56px（替代值 48px 更保守）
- service-row padding 是否要動（可選擇不動，做更保守的保守版）

---

## 10. 執行步驟

1. 在 DevTools 直接 inject `.section-intro .kicker::before` 試一次，確認短橫線位置正確。
2. 寫入 `index.html` 的 `<style>` 區段，依 §4 與 §5 順序。
3. 桌機檢查 6 個 section（What I Build、Labs、How It Works、Automation、Services、Contact）短橫線都正確出現在 kicker 上方。
4. 920px viewport 確認沒有 horizontal overflow，短橫線縮放合理。
5. 640px viewport 確認 mobile override 生效（線縮短到 28px）。
6. 375px viewport 額外確認 iPhone SE 級寬度沒有任何 overflow。
7. 確認 Hero `.eyebrow` 完全沒有受影響（不應該長出短橫線）。
8. 確認 About 段沒有出現短橫線（因為 About 沒有 `.section-intro`）。
9. 不 build / 不 deploy / 不 commit，由使用者決定何時 push。

---

## 11. 後續可能性

本輪完成後，可重新評估的下一步（**不在本輪範圍內**）：

- 短橫線是否推廣到 Works case study 內頁（待 Phase 2）。
- Automation `automation-wrap` 容器簡化（方案 B）。
- SPP Foundry 自己的小 mark 設計（不照抄 Google sparkle）。
- Hero 右側 SVG 重新收斂。
- Labs 從「卡片」改成「橫條」的長期演進。

這些都是未來討論題，本輪不執行。

---

## 12. Scope 邊界（再次確認）

可以做：

- 修改根目錄 `index.html` 的 `<style>` 區段
- 純 CSS 變更
- DevTools 試做與微調

不要做：

- 不改 `/labs/flow-booking/**`
- 不改 `/labs/aicert/**`
- 不新增 build pipeline
- 不新增 `/works/`、`/services/`、`/articles/` 頁面
- 不 build、不 deploy、不 commit（除非使用者明確要求）
- 不動 HTML 結構
- 不動 `:root` color tokens
- 不動 button 系統
- 不引入新 SVG / icon / 動畫

---

© SPP Foundry · v1.0 · Visual Refinement Plan · 2026-05-08
