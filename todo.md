# XuanLin 網站優化 Todo

## 高優先（效能）

- [x] 將 `index.html`、`cases.html`、`xuan-lin-en.html` 中的 base64 圖片全部替換為外部檔案路徑（使用 `state/` 資料夾中的照片）
- [x] 壓縮 `state/` 資料夾中的照片（JPEG quality 80；WebP 需另外安裝 cwebp 工具）

## 中優先（維護性）

- [ ] 建立 `style.css`，將三個頁面重複的 CSS 抽出共用
- [ ] 建立 `main.js`，將 scroll reveal 動畫、漢堡選單邏輯抽出共用

## 低優先（SEO）

- [ ] 每個頁面補上 `<meta name="description">` 標籤
- [ ] 每個頁面補上 Open Graph meta tags（`og:title`、`og:description`、`og:image`），讓 LINE / Facebook 分享時有預覽圖
