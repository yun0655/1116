# 書路 Bookway 圖書館跨館找書與登入助手

本儲存庫包含網站前端原型、產品需求文件及圖書館登入／借閱資格整理。

## Firebase Google 登入設定

網站已加入 Google 登入介面與 Firebase Authentication 前端整合。要讓登入真正可用，請先在 Firebase Console 完成以下設定：

1. 建立 Firebase 專案，新增 Web App，複製 `firebaseConfig`。
2. 在 Authentication → Sign-in method 啟用 Google provider。
3. 在 Authentication → Settings → Authorized domains 加入 `yun0655.github.io`。
4. 將 Web App 設定值填入 `index.html` 內的 `FIREBASE_CONFIG`，或部署前提供 `window.BOOKWAY_FIREBASE_CONFIG`。
5. 推送變更後等待 GitHub Pages 部署完成，再測試 Google 登入與登出。

Firebase Web API key 是用戶端設定值，不是伺服器密碼；資料存取安全仍需設定 Firebase Security Rules。此版本只有身分驗證，不會把使用者資料同步到 Firebase，也不會收集圖書館密碼；常用圖書館設定仍存在瀏覽器本機。

## 其他檔案
- `index.html`：單頁網站原型。館藏查詢結果為示範資料，非全台即時館藏 API。
- `library-access-guide.md`：代表性公共與大學圖書館的登入方式、資格與官方來源。
- `PRD_圖書館跨館找書與登入助手.docx`：Word 格式 PRD。
- `PRD_圖書館跨館找書與登入助手.txt`：純文字 PRD。

直接以瀏覽器開啟 `index.html` 可查看前端原型。
