# 書路 Bookway 圖書館跨館找書與登入助手

本儲存庫包含網站前端原型、產品需求文件及圖書館登入／借閱資格整理。

## Firebase 登入與 Firestore 同步

網站使用 Firebase 專案 `bookway-1f1d9`，Web App 名稱為 `Bookway Web`。Google 登入供應商已啟用，並已將 `yun0655.github.io` 加入授權網域。Firebase Web 設定已放入 `index.html` 與 `firebase-config.js`。

Firestore Enterprise Native Mode 資料庫 `bookway` 位於 `asia-east1`。登入後，「我的圖書館」會同步至 `users/{uid}/libraries/{libraryId}`；每筆只包含圖書館名稱、網址、帳號格式提示與個人提示，不儲存密碼。未登入時資料保存在瀏覽器本機；首次登入且雲端清單為空時，會將本機清單同步到該帳號。`firestore.rules` 限制登入者只能讀寫自己的資料。Enterprise 資料庫依使用量計費。

GitHub Pages 從 `main` 分支根目錄發布：[書路 Bookway](https://yun0655.github.io/1116/)。推送至 `main` 後會自動重新部署。

Firebase Web API key 是用戶端設定值，不是伺服器密碼；資料存取由 Firebase Authentication 與 Firestore Security Rules 保護。網站不會收集圖書館密碼。

## 其他檔案
- `index.html`：單頁網站原型。館藏查詢結果為示範資料，非全台即時館藏 API。
- `library-access-guide.md`：代表性公共與大學圖書館的登入方式、資格與官方來源。
- `PRD_圖書館跨館找書與登入助手.docx`：Word 格式 PRD。
- `PRD_圖書館跨館找書與登入助手.txt`：純文字 PRD。

直接以瀏覽器開啟 `index.html` 可查看前端原型。
