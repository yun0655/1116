# 書路 Bookway 圖書館跨館找書與登入助手

本儲存庫包含網站前端原型、產品需求文件及圖書館登入／借閱資格整理。

## Firebase 登入與 Firestore 同步

網站使用 Firebase 專案 `bookway-1f1d9`，Web App 名稱為 `Bookway Web`。Google 登入供應商已啟用，並已將 `yun0655.github.io` 加入授權網域。Firebase Web 設定已放入 `index.html` 與 `firebase-config.js`。

Firestore Enterprise Native Mode 資料庫 `bookway` 位於 `asia-east1`。登入後，「我的圖書館」會同步至 `users/{uid}/libraries/{libraryId}`；每筆只包含圖書館名稱、網址、帳號格式提示與個人提示，不儲存密碼。未登入時資料保存在瀏覽器本機；首次登入且雲端清單為空時，會將本機清單同步到該帳號。`firestore.rules` 限制登入者只能讀寫自己的資料。Enterprise 資料庫依使用量計費。

GitHub Pages 從 `main` 分支根目錄發布：[書路 Bookway](https://yun0655.github.io/1116/)。推送至 `main` 後會自動重新部署。

Firebase Web API key 是用戶端設定值，不是伺服器密碼；資料存取由 Firebase Authentication 與 Firestore Security Rules 保護。網站不會收集圖書館密碼。

## AI 找書助理

首頁的「AI 找書助理」使用 Firebase AI Logic 與 Gemini 3.8 Flash，將自然語言需求整理成書目搜尋詞與實體／電子書篩選條件。讀者輸入的描述會送到 Gemini 處理，不會寫入 Bookway 的 Firestore。助理只整理搜尋條件；目前館藏仍是示範資料，不是全台即時查詢。

啟用前，在本專案目錄使用已登入 Firebase 的 CLI 執行 `npx -y firebase-tools@latest init ailogic`，為 Firebase 專案啟用 AI Logic。接著在 Firebase Console 為 `Bookway Web` 設定 App Check（reCAPTCHA Enterprise），把公開 site key 填入 `index.html` 的 `FIREBASE_APPCHECK_SITE_KEY`。AI Logic 對網頁呼叫會要求有效的 App Check token；未完成這兩項設定前，助理介面會提示尚未啟用。

## 其他檔案
- `index.html`：單頁網站原型。館藏查詢結果為示範資料，非全台即時館藏 API。
- `library-access-guide.md`：代表性公共與大學圖書館的登入方式、資格與官方來源。
- `PRD_圖書館跨館找書與登入助手.docx`：Word 格式 PRD。
- `PRD_圖書館跨館找書與登入助手.txt`：純文字 PRD。

直接以瀏覽器開啟 `index.html` 可查看前端原型。
