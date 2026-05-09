# 交易紀錄網頁

這個資料夾包含兩個主要檔案：

- `trading-journal.html`
- `google-apps-script.js`

## 使用方式

1. 把 `google-apps-script.js` 貼到你的 Google Apps Script 專案。
2. Google Sheet 建議工作表名稱設成 `交易日誌`。
3. 第一列欄位會自動建立為：
   `id | date | symbol | result | rr | session | note | imgs`
4. Apps Script 部署成「網頁應用程式」。
   - 執行身分：你自己
   - 存取權：所有人
5. 如果你重新部署後網址變了，把 `trading-journal.html` 裡的 `API_URL` 換成新網址。
6. 將 `trading-journal.html` 放到任何靜態空間都可以開：
   - 直接雙擊本機檔案
   - 丟到 GitHub Pages / Netlify / Vercel
   - 放到自己的 HTTP 網站

## 這版修正重點

- 修正月份分隔列塞進 `<tbody>` 的無效 HTML 結構
- 新增「總 RR」欄位，顯示每筆交易在當前清單中的累積 RR
- 補上文字內容轉義，避免備註或商品名稱破版
- 圖片支援點擊、拖曳、貼上，並先縮圖壓縮再同步
- Apps Script 不再硬綁 `工作表1`，會自動建立或使用 `交易日誌`
- Apps Script 增加鎖，減少多裝置同時寫入時互相覆蓋的風險

## 注意

把圖片直接存成 base64 放進 Google Sheets 仍然有容量限制，這種做法適合少量截圖紀錄。如果你之後想放很多大圖，下一步比較建議把圖片改存到 Google Drive，只把圖片連結寫進 Sheet。
