# 🚕 NoBodyPay 計程車跳表

台灣與澳洲（QLD 昆士蘭）雙地區計程車跳表模擬器，純前端網頁、無需安裝、無後端伺服器，可加入手機主畫面當作 App 使用。

🔗 **線上使用：** `https://<你的GitHub帳號>.github.io/<repo名稱>/`
（部署完成後請把這行換成你的實際網址）

---

## ✨ 功能

- **雙地區計費**
  - 🇹🇼 台灣：起跳 $85（含前 1.25km）、之後每 200m +$5、低速（<5km/h）每分鐘 +$5、夜間加成 +$20、高速公路每按一次 +$40
  - 🇦🇺 澳洲 QLD：採用昆士蘭交通部公告費率（起跳費依日間/其他時段、每公里依南東昆士蘭／地區型／偏遠地區三種分區、候車每分鐘計費）
- **計費模式**：模擬車速拉桿，或使用手機 GPS 實際定位計算移動距離與速度
- **多人共乘分攤**：可新增多位乘客，分別記錄各自上下車時間，自動依「同時上下車平均分攤」或「依各自實際搭乘時間比例分攤」計算車資
- **友情價折扣**：可對個別乘客套用百分比或固定金額折扣，折扣由司機吸收、不轉嫁給其他乘客
- **行程記錄**：每次停止行程自動記錄一筆，可在面板中查看或刪除，保存在瀏覽器本機
- **記住上次設定**：地區、計費模式、夜間加成、QLD 分區、模擬車速、螢幕恆亮等設定會自動記住
- **收據圖片分享**：用原生 Canvas 產生收據圖片，透過手機系統分享選單直接傳送或存到相簿
- **直式／橫式雙版面**：直式滿版顯示，橫式維持儀表板卡片風格
- **可加入主畫面**：支援 iOS/Android「加入主畫面」變成全螢幕 App 體驗

## ⚠️ 重要限制（請務必詳閱）

- **這是一個計費模擬／教學／個人記帳用途的工具，不是合法的計程車計費器**，不能用來作為向乘客收費的正式依據。台灣與澳洲對計程車計費表（taxi meter）的安裝、校驗、認證皆有法規要求，本專案純為軟體模擬，未經任何計量單位校驗認證。
- **GPS 定位功能需要瀏覽器原生支援**，且必須在獨立瀏覽器分頁中開啟（不能在某些 App 內建的 WebView/iframe 預覽環境中使用，否則瀏覽器不會跳出定位授權請求）。
- **資料儲存在瀏覽器本機（localStorage）**，僅限同一台裝置、同一個瀏覽器有效。清除瀏覽器資料、換瀏覽器、換裝置都會遺失行程記錄與設定，本專案沒有雲端同步或帳號系統。
- 澳洲 QLD 費率為 2025/7/1 公告生效之費率，台灣費率為市區常見費率之示意值，兩者皆僅供參考，實際費率請以當地監理機關／計程車業者公告為準，且費率可能隨時間調整。

## 📁 檔案結構

```
repo/
├── index.html              ← 主程式（GitHub Pages 預設首頁）
├── manifest.json            ← PWA 設定（Android 加入主畫面用）
├── apple-touch-icon.png     ← iOS 加入主畫面圖示 (180×180)
├── favicon.ico               ← 瀏覽器分頁圖示（相容舊版）
├── favicon-32x32.png
├── favicon-16x16.png
├── icons/
│   ├── icon-192.png          ← Android PWA 圖示
│   └── icon-512.png          ← Android PWA 圖示（高解析度）
├── README.md
├── LICENSE
└── .gitignore
```

## 🎨 更換 App 圖示

如果之後想換掉圖示，準備好新圖後，依序替換以下檔案（**檔名要完全一樣**才會被網頁正確讀取）：

| 檔案 | 用途 | 建議尺寸 |
|---|---|---|
| `apple-touch-icon.png` | iPhone/iPad 加入主畫面 | 180×180 |
| `icons/icon-192.png` | Android 加入主畫面 | 192×192 |
| `icons/icon-512.png` | Android 加入主畫面（高解析度） | 512×512 |
| `favicon-32x32.png` / `favicon-16x16.png` / `favicon.ico` | 瀏覽器分頁小圖示 | 32×32 / 16×16 |

替換後直接在 GitHub 網頁上傳同名檔案覆蓋即可（上傳方式同更新 `index.html` 的步驟），不需要改 `index.html` 或 `manifest.json` 的程式碼，因為都是用檔名對應的。

> 小提醒：瀏覽器跟手機系統對圖示有快取，換完圖示後如果手機上看起來沒變，試著把已加入主畫面的捷徑刪除、清除 Safari/Chrome 快取，再重新「加入主畫面」一次。

## 🚀 部署到 GitHub Pages

1. 在 GitHub 建立一個新的 repository（公開或私人皆可，私人 repo 需 Pro 方案才能用 Pages）
2. 把這個資料夾的內容（至少 `index.html`）推上去：

   ```bash
   git init
   git add .
   git commit -m "Initial commit: taxi meter app"
   git branch -M main
   git remote add origin https://github.com/<你的帳號>/<repo名稱>.git
   git push -u origin main
   ```

3. 到 repo 的 **Settings → Pages**
4. 在 **Build and deployment → Source** 選擇 `Deploy from a branch`
5. **Branch** 選擇 `main`，資料夾選擇 `/ (root)`，按 **Save**
6. 等待約 1-2 分鐘，GitHub 會提供一個網址，格式為：
   `https://<你的帳號>.github.io/<repo名稱>/`
7. 用手機瀏覽器（非預覽/WebView）開啟該網址即可使用，GPS 與分享功能都需要在這個正式網址下才能正常運作（localhost 與 https 網域可以用，純 iframe 預覽不行）

> 之後每次 `git push` 到 `main` 分支，GitHub Pages 會自動重新部署，通常 1 分鐘內生效。

## 📱 加入手機主畫面（變成全螢幕 App）

- **iPhone (Safari)：** 開啟網址 → 點選分享圖示 → 「加入主畫面」
- **Android (Chrome)：** 開啟網址 → 右上角選單 → 「加入主畫面」/ 「安裝應用程式」

加入主畫面後從主畫面圖示開啟，會以全螢幕模式顯示（無網址列）。

## 🛠 技術說明

- 純原生 HTML / CSS / JavaScript，單一檔案 `index.html`，無任何外部 CDN 或函式庫依賴，離線也能運作（部署後可加上 Service Worker 做完整 PWA 離線快取，目前未包含）
- 收據圖片用原生 Canvas API 繪製，不依賴截圖或外部繪圖函式庫
- 定位使用瀏覽器原生 `navigator.geolocation`
- 分享使用瀏覽器原生 Web Share API (`navigator.share`)，不支援的環境會自動 fallback 為下載
- 資料持久化使用瀏覽器原生 `localStorage`，無任何後端或第三方服務

## 📄 授權

本專案採用 [MIT License](./LICENSE)，歡迎自由使用、修改、散布。

## 🙏 免責聲明

本工具僅供個人模擬、教育、娛樂用途，所有費率僅供參考，作者不對因使用本工具產生的任何費用爭議或計費錯誤負責。實際計程車收費請以合法計費表與當地法規為準。
