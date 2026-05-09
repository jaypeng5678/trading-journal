# 交易紀錄網頁

這是一個可同步到 Google Sheets 的交易紀錄網頁，適合用來記錄每筆交易的商品、勝負、RR、交易時段、文字備註和截圖，並可在電腦與手機上共用。

## 主要檔案

- `trading-journal.html`
- `google-apps-script.js`
- `index.html`

## 功能

- 新增、編輯、刪除交易紀錄
- 欄位包含：
  - 商品名稱
  - 贏 / 輸
  - RR
  - 總 RR
  - 交易時段
  - 文字紀錄
  - 圖片上傳
- 圖片支援：
  - 點選上傳
  - 拖曳上傳
  - 直接貼上圖片
- 資料同步到 Google Sheets，可跨裝置共用
- `全部交易` 分頁：
  - 依月份分組
  - 顯示每月筆數、W/L、月總 RR
- `月份交易` 分頁：
  - 月曆顯示每日交易筆數與當日 RR
  - 可點選日期查看當日勝率與交易明細
  - 可切換查看過去月份
  - 每週右側顯示到週六的當周總 RR

## 部署 Google Sheets 後端

1. 建立一份 Google 試算表
2. 打開 `擴充功能 > Apps Script`
3. 把 `google-apps-script.js` 內容貼進去
4. 儲存後部署成 `網頁應用程式`
5. 權限設定：
   - 執行身分：你自己
   - 存取權：所有人
6. 複製部署後的網址
7. 打開 `trading-journal.html`
8. 把 `API_URL` 改成你的 Apps Script 網址

## 欄位格式

Apps Script 會自動建立以下欄位：

`id | date | symbol | result | rr | session | note | imgs`

## 本機使用

可以直接雙擊 `trading-journal.html` 用瀏覽器開啟。

## GitHub Pages

如果要讓手機直接透過網址開啟：

1. 上傳 `index.html` 和 `trading-journal.html` 到 GitHub repository 根目錄
2. 到 `Settings > Pages`
3. `Source` 選 `Deploy from a branch`
4. `Branch` 選 `main`
5. 資料夾選 `/ (root)`

部署完成後就會得到公開網址，例如：

`https://你的帳號.github.io/trading-journal/`

## 備註

- 圖片目前是以 base64 形式存在 Google Sheets
- 少量截圖沒問題，但如果之後圖片很多，建議改成把圖片存到 Google Drive，只在 Sheet 存連結
- 如果重新部署 Apps Script，記得同步更新 `trading-journal.html` 裡的 `API_URL`
