# 神魔之塔龍刻圖鑑

一個響應式的《神魔之塔》龍刻與武裝龍刻圖鑑，可依編號、類型、模式、圖片狀態及收藏狀態進行搜尋與篩選。

本專案是非官方粉絲工具，與《神魔之塔》官方及 Mad Head Limited 無關。遊戲名稱、圖片及相關資料的權利屬原權利人所有。

## 功能

- 收錄一般龍刻與武裝龍刻資料
- 依編號由小到大或由大到小排序
- 依龍刻類型、模式及收藏狀態篩選
- 搜尋編號、名稱、技能或適用角色
- 查看龍刻技能、武裝能力與裝備條件
- 使用電子郵件與密碼註冊、登入及重設密碼
- 登入後標記已擁有、未擁有或待確認，並跨裝置同步
- 離線時暫存變更，恢復連線後自動重試
- 將收藏紀錄匯出及匯入為 JSON 備份
- 從五欄遊戲背包影片輔助辨識擁有狀態
- 響應式介面：桌面每列 5 張、平板每列 3 張、手機每列 2 張

## 使用方式

直接開啟 `index.html` 即可瀏覽。帳號與跨裝置同步使用 Supabase；尚未設定時會保持停用，圖鑑瀏覽不受影響。設定步驟請見 [`SUPABASE_SETUP.md`](SUPABASE_SETUP.md)。

登入後，收藏會同步至自己的 Supabase 帳號；瀏覽器同時保留帳號專屬快取與離線待辦。JSON 匯出仍可作為額外備份。

## 使用 GitHub Pages 發布

1. 在 GitHub 建立一個新的公開 Repository，例如 `tos-dragonware`。
2. 將 `index.html` 和本 `README.md` 上傳到 Repository 根目錄。
3. 開啟 Repository 的 **Settings → Pages**。
4. 在 **Build and deployment** 將 Source 設為 **Deploy from a branch**。
5. Branch 選擇 **main**，資料夾選擇 **/(root)**，然後按下 **Save**。
6. 發布完成後，網站網址通常為：

   ```text
   https://你的GitHub帳號.github.io/tos-dragonware/
   ```

從本機版改用公開網址時，瀏覽器會視為不同網站，因此請先從本機版匯出收藏，再到公開版匯入。

## 未來更新資料

遊戲新增龍刻後，可提供以下資料更新圖鑑：

- 背包列表影片：辨識編號、圖片及是否擁有
- 龍刻詳情畫面：確認名稱、模式、技能與裝備條件
- 官方更新公告或可靠的資料來源

更新完成後，只要在 GitHub Repository 中替換 `index.html` 並提交變更，GitHub Pages 就會重新發布網站。既有龍刻會保留穩定的收藏識別碼，讓舊的收藏備份可以繼續使用。

## 資料與圖片來源

主要資料整理自：

- [蒼曜（tinghan33704）神魔之塔工具們](https://github.com/tinghan33704/tos-tools)
- [hiteku 武裝龍刻搜尋器](https://hiteku.github.io/tosCrafts/)
- 使用者提供的遊戲背包畫面

部分同名龍刻的不同模式共用同一張圖片。實際技能、取得方式、分數門檻及遊戲調整請以遊戲內最新資訊為準。

## 隱私提醒

- 影片會在瀏覽器本機處理，不會由本網站上傳到伺服器。
- 請勿將原始遊戲錄影、帳號畫面或個人收藏備份提交到公開 Repository。
- 收藏備份可能反映個人遊戲進度，分享前請自行確認內容。
- 雲端只保存使用者修改過的龍刻識別碼與收藏狀態；資料表以 Row Level Security 隔離帳號。
- 網頁只可放 Project URL 與 Publishable key，不得放 service role key、secret key、資料庫密碼或 SMTP 密碼。

## 專案檔案

```text
index.html  # 完整網站，包含 HTML、CSS、JavaScript 與圖鑑資料
README.md   # 專案說明
SUPABASE_SETUP.md # 帳號與雲端同步設定步驟
```

## 技術說明

- 純 HTML、CSS 與 JavaScript
- 原始資料由 `python3 work/build.py` 產生單一 `index.html`
- 登入與收藏同步使用 Supabase Auth/Postgres
- 離線快取使用帳號隔離的 `localStorage`
- 可直接部署至 GitHub Pages 等靜態網站服務

## 部署順序

1. 先依 [`SUPABASE_SETUP.md`](SUPABASE_SETUP.md) 建立 Supabase 並執行資料表設定。
2. 填入公開的 Project URL 與 Publishable key，重新產生 `index.html`。
3. 發布到 GitHub Pages，再把正式網址加入 Supabase Site URL 與 Redirect URLs。
4. 以兩個測試帳號完成權限及跨裝置驗證。
