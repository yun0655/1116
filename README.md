# 書路 Bookway 圖書館跨館找書與登入助手

本儲存庫包含網站前端原型、產品需求文件及圖書館登入／借閱資格整理。

## Firebase Google 登入設定

網站使用 Firebase 專案 `bookway-1f1d9`，Web App 名稱為 `Bookway Web`。Google 登入供應商已啟用，並已將 `yun0655.github.io` 加入授權網域。Firebase Web 設定已放入 `index.html` 與 `firebase-config.js`。

GitHub Pages 從 `main` 分支根目錄發布：[書路 Bookway](https://yun0655.github.io/1116/)。推送至 `main` 後會自動重新部署。

Firebase Web API key 是用戶端設定值，不是伺服器密碼；資料存取安全仍需設定 Firebase Security Rules。此版本只有身分驗證，不會把使用者資料同步到 Firebase，也不會收集圖書館密碼；常用圖書館設定仍存在瀏覽器本機。

## 其他檔案
- `index.html`：單頁網站原型。館藏查詢結果為示範資料，非全台即時館藏 API。
- `library-access-guide.md`：代表性公共與大學圖書館的登入方式、資格與官方來源。
- `PRD_圖書館跨館找書與登入助手.docx`：Word 格式 PRD。
- `PRD_圖書館跨館找書與登入助手.txt`：純文字 PRD。

直接以瀏覽器開啟 `index.html` 可查看前端原型。
