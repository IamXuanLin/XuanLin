# XuanLin 個人品牌網站 — 專案規則

## 專案簡介

Xuan Lin 的個人品牌網站，定位為「國際展務專案經理」。
純靜態網站，無框架、無建置工具，直接用瀏覽器開啟即可。

---

## 檔案結構

網站檔案全部放在 `docs/` 資料夾下（GitHub Pages 從此資料夾部署）。

```
XuanLin/
├── CLAUDE.md
├── README.md
└── docs/                       # ← 網站根目錄
    ├── index.html              # 主頁（繁體中文版）
    ├── xuan-lin-en.html        # 主頁（英文版）
    ├── cases.html              # 案例作品集（中文）
    ├── cases-en.html           # 案例作品集（英文）
    ├── resume.html             # 履歷（中文）
    ├── resume-en.html          # 履歷（英文）
    ├── favicon.svg
    ├── css/
    │   └── style.css           # 共用樣式（index + xuan-lin-en 共用）
    ├── js/
    │   └── main.js             # 共用 JS（scroll reveal、hamburger、navbar shadow）
    └── images/
        ├── xuan-logo-v2.svg
        └── photos/             # 所有展覽照片（WebP 格式）
            ├── 新加坡_1.webp ～ 新加坡_6.webp
            ├── 新加坡_互動.webp
            └── 香港_1.webp ～ 香港_3.webp
```

---

## 語言版本對應

| 中文 | 英文 | 說明 |
|---|---|---|
| `index.html` | `xuan-lin-en.html` | 主頁 |
| `cases.html` | `cases-en.html` | 案例作品集 |
| `resume.html` | `resume-en.html` | 履歷 |

- 中文頁的「回首頁」連到 `index.html`，英文頁連到 `xuan-lin-en.html`
- `index.html` 的 about-highlight-link → `resume.html`
- `xuan-lin-en.html` 的 about-highlight-link → `resume-en.html`
- `xuan-lin-en.html` 的 Cases 連結（桌機 nav + 手機 menu）→ `cases-en.html`

---

## CSS 架構

- `docs/css/style.css`：`index.html` 和 `xuan-lin-en.html` **共用**的樣式。
- 其餘四個頁面（cases、cases-en、resume、resume-en）各自有 **inline `<style>`**，不使用 style.css。

### 修改樣式的原則

| 要改的東西 | 改哪裡 |
|---|---|
| 顏色變數、字型、nav、hero、about、contact | `docs/css/style.css` |
| index.html 的 service / process / trust 區塊 | `docs/index.html` 的 `<style>` |
| 英文版的 bring / highlights 區塊 | `docs/xuan-lin-en.html` 的 `<style>` |
| 案例頁的所有樣式 | `docs/cases.html` 或 `docs/cases-en.html` 的 `<style>` |
| 履歷頁的所有樣式 | `docs/resume.html` 或 `docs/resume-en.html` 的 `<style>` |

---

## 設計系統

### 色彩

```css
--navy: #0D1B2A       /* 主色，深海軍藍 */
--navy-mid: #1A2D42
--gold: #C9A84C       /* 強調色，金色 */
--gold-light: #E2C97E
--gold-pale: #F5EDD6  /* 淺金背景 */
--bg: #F8F9FB         /* 頁面底色 */
--bg2: #EEF1F5
--text: #2C3E50
--text-mid: #4A5568
--text-light: #718096
```

### 字型

- **標題 / 數字**：`Cormorant Garamond`（serif，優雅氣質）
- **內文 / UI**：`Noto Sans TC`（sans-serif，中英文通用）
- 兩者都從 Google Fonts CDN 載入，使用**非阻塞方式**（`rel="preload" as="style" onload`）
- Noto Sans TC 只載入 3 個字重：`400;500;700`（移除 300、900 以減少下載量）

### 間距慣例

- 桌面版 section padding：`5.5rem 2.5rem`
- 手機版 section padding：`3.5rem 1.25rem`
- 最大內容寬度：`max-width: 1020px`
- RWD 斷點：`768px`

---

## JS 架構

`docs/js/main.js` 包含三個功能，所有頁面共用：

1. **Navbar scroll shadow**：滾動超過 20px 時加 `.scrolled` class（cases、resume 系列頁無此功能，因 nav 固定有 shadow）
2. **Hamburger menu**：切換 `.open` class（cases、resume 系列頁無漢堡選單）
3. **Scroll reveal**：`.reveal` 元素進入視窗時加 `.visible` class，帶有 stagger delay

`cases.html` 和 `cases-en.html` 另外有 lightbox 功能，inline 寫在頁面底部。

---

## 圖片規則

- 所有照片統一存放於 `docs/images/photos/`，格式為 **WebP**，quality 80。
- 新加坡照片：`新加坡_1.webp` ～ `新加坡_6.webp`、`新加坡_互動.webp`
- 香港照片：`香港_1.webp` ～ `香港_3.webp`
- Logo：`docs/images/xuan-logo-v2.svg`
- **不要**用 base64 嵌入圖片，一律用外部路徑引用。
- 首屏以下的圖片一律加 `loading="lazy"`。
- 新增照片請先用 sharp（Node.js）或 Squoosh 壓縮成 WebP，再放入 `docs/images/photos/`。
- `新加坡_6.webp` 目前未在任何頁面引用，保留備用。

---

## 聯絡資訊（頁面中使用）

- Email：`mialin1220@gmail.com`
- Instagram：`@hxuan_er`
- 電話：`+886 910-978-753`（僅履歷頁使用）

---

## 注意事項

- 所有網站檔案都在 `docs/` 底下，修改時路徑要從 `docs/` 開始找。
- 修改 `docs/css/style.css` 會同時影響 `index.html` 和 `xuan-lin-en.html`，請確認兩頁的呈現都正常。
- `cases.html` 的 `.photo-thumb:hover img` 使用 `scale(1.06)`，與其他頁面的 `scale(1.05)` 略有不同，是刻意設計。
- 內容更動時記得同步更新對應的中英文版本（共 3 組語言對）。
- cases-en.html 和 resume-en.html 的 nav「← Back」連回英文主頁 `xuan-lin-en.html`。
