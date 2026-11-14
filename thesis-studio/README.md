# 論文寫作工作臺

## 直接開始

1. 在「我的歷年論文」上傳自己撰寫的 PDF。勾選代表作，或讓模型依稿件語言、類型與研究設計選擇。
2. 在「研究文獻」上傳從 ScienceDirect 下載、與本題相關的 PDF。
3. 填入論文題目、研究設定及本次要求。預設交付繁體中文的緒論與文獻探討，使用 APA 第 7 版。
4. 選擇一種輸出方式。
   - **產生 ChatGPT 指令**。複製指令到 ChatGPT，同時上傳列出的 PDF。本機 PDF 可用原檔或下載帶有 S／R 編號的版本。這條路徑無須 API 金鑰。
   - **用 Gemini 生成初稿**。在「使用 Gemini 直接生成」輸入個人的 Gemini API 金鑰，再按生成。網頁會把勾選的 PDF 與要求送到 Google Gemini API。可用模型視帳戶而異，請以 Google AI Studio 顯示的模型 ID 為準。每次送出後會清空金鑰欄位。此模式的 PDF 合計上限為 30 MiB。
5. 編修輸出，或下載 Markdown。請回到原文核對重要引文、頁碼與 DOI。

## 連接兩個 Google Drive 資料夾

1. 在 [Google Cloud Console](https://console.cloud.google.com/) 建立或選擇專案並啟用 **Google Drive API**。
2. 設定 **Google Auth Platform** 的品牌與目標對象。若使用外部測試模式，將會使用本工具的 Google 帳號加入測試使用者。此流程使用 `https://www.googleapis.com/auth/drive.readonly` 唯讀權限。若學校帳號受管理員限制，可改用本機上傳。
3. 在 **用戶端** 建立 OAuth 2.0 用戶端，類型選「網頁應用程式」。在「已授權的 JavaScript 來源」加入 `https://tnyenningsu.github.io`。只填網域來源，省略 `/web/thesis-studio/` 路徑。
4. 將用戶端 ID 貼到工作臺，按「授權讀取」。用戶端 ID 以 `.apps.googleusercontent.com` 結尾。
5. 分別貼上歷年論文與研究文獻資料夾連結，按「讀取 PDF 清單」。工具會列出資料夾與子資料夾中的 PDF。勾選本次要用的文件。

網站直接使用你的 Google 授權讀取 PDF，資料夾可維持私有。程式碼託管於 GitHub Pages。工具本身不會將 PDF、Google 授權或 API 金鑰寫入 GitHub 或瀏覽器的持久儲存。請用個人金鑰及你有權交給所選 AI 服務處理的文件。關閉或重新整理頁面前，請下載需要保留的稿件。
