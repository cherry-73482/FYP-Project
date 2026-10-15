# MindAnchor 專案說明

MindAnchor 是一個結合 AI 聊天、學習模組、社工分流和老師儀表板的校園心理健康與學習支援系統。

本專案使用：

- React：前端
- Node.js + Express：後端 API
- MySQL：資料庫
- phpMyAdmin：管理 MySQL 資料庫
- Git + GitHub：多人協作

## 專案結構

```text
mindanchor/
├─ client/       React 前端
├─ server/       Node.js + Express 後端
├─ database/     SQL 檔案
└─ README.md
```

## 第一次使用前要下載的軟件

每位組員都需要安裝以下軟件：

| 軟件 | 用途 | 下載網址 |
|---|---|---|
| Node.js LTS | 執行 React 和 Express | https://nodejs.org/ |
| Git | 下載和上傳專案 | https://git-scm.com/ |
| XAMPP | 提供 Apache、MySQL 和 phpMyAdmin | https://www.apachefriends.org/ |
| Postman | 測試後端 API | https://www.postman.com/downloads/ |

安裝完成後，打開 VS Code Terminal 檢查：

```bash
node -v
npm -v
git --version
```

如果每個指令都顯示版本號，代表環境已準備好。

## 如何用 Git 下載專案

### 1. 建立 GitHub 帳號

如果還沒有 GitHub 帳號，先到以下網址註冊：

https://github.com/

### 2. Clone 專案

打開 VS Code，選擇：

```text
File > Open Folder
```

選擇你想存放專案的資料夾，例如：

```text
D:\FYP
```

然後打開 Terminal，輸入：

```bash
git clone https://github.com/cherry-73482/FYP-Project.git
cd cd FYP-Project
```

### 3. 安裝前端依賴

```bash
cd client
npm install
```

### 4. 安裝後端依賴

另開一個 Terminal，或先回到專案根目錄：

```bash
cd ..
cd server
npm install
```

## 如何啟動 MySQL 和 phpMyAdmin

1. 打開 **XAMPP Control Panel**
2. 按 **Start** 啟動 `Apache`
3. 按 **Start** 啟動 `MySQL`
4. 在瀏覽器打開：

```text
http://localhost/phpmyadmin
```

如果成功看到 phpMyAdmin 頁面，代表資料庫已啟動。

## 如何匯入資料庫

1. 打開 `http://localhost/phpmyadmin`
5. 按上方 **Import**
6. 選擇專案內的 SQL 檔案，例如：

```text
database/mindanchor.sql
```
```sql
我晚點會做那個 SQL 檔，讓你們可以下載
```

## 如何設定後端 `.env`

在 `server/` 資料夾建立 `.env` 檔案：

```env
PORT=5000
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=
DB_NAME=mindanchor
JWT_SECRET=change_this_to_a_long_random_secret
```

注意：

- XAMPP 的 MySQL 預設帳號是 `root`
- XAMPP 的 MySQL 預設密碼通常是空白
- 如果你的 MySQL 有密碼，請填入 `DB_PASSWORD=你的密碼`
- `.env` 不可以上傳到 GitHub

同時建立 `.env.example`：

```env
PORT=5000
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=mindanchor
JWT_SECRET=your_jwt_secret
```

## 如何啟動前端和後端

### 啟動後端

在 `server/` Terminal 輸入：

```bash
npm run dev
```

如果沒有設定 `npm run dev`，可使用：

```bash
node server.js
```

成功後會顯示：

```text
Server running on http://localhost:5000
```

### 啟動前端

另開一個 Terminal，進入 `client/`：

```bash
cd client
npm run dev
```

成功後打開：

```text
http://localhost:5173
```

## 每次繼續做專案的流程

每次開始工作前，先更新最新代碼：

```bash
git checkout main
git pull origin main
```

然後建立自己的功能分支：

```bash
git checkout -b feature/你的功能名稱
```

例如：

```bash
git checkout -b feature/student-chat
git checkout -b feature/teacher-dashboard
git checkout -b feature/login-api
```

完成功能後：

```bash
git add .
git commit -m "Add student chat page"
git push origin feature/你的功能名稱
```

然後到 GitHub 建立 **Pull Request**，請另一位組員 review 後才合併到 `main`。

## 組員更新了代碼後要做什么

如果另一位組員新增了 npm 套件，先拉取最新代碼：

```bash
git pull origin main
```

然後分別在 `client/` 和 `server/` 執行：

```bash
npm install
```

不需要重新輸入所有套件名稱，因為 `package.json` 已記錄所有依賴。

## 第一次打開專案常見錯誤

### 1. `npm : 因為這個系統上已停用指令碼執行`

這是 Windows PowerShell 安全政策問題。

解決方法：

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

輸入：

```text
Y
```

然後關閉 Terminal，重新開啟，再執行：

```powershell
npm -v
```

### 2. `npm is not recognized`

代表 Node.js 未安裝，或安裝後沒有重啟 Terminal。

解決方法：

1. 安裝 Node.js LTS
2. 關閉 VS Code
3. 重新打開 VS Code
4. 再測試：

```bash
node -v
npm -v
```

### 3. `Cannot find module 'express'`

代表後端依賴未安裝。

解決方法：

```bash
cd server
npm install
```

### 4. `Cannot find module 'react'`

代表前端依賴未安裝。

解決方法：

```bash
cd client
npm install
```

### 5. `ECONNREFUSED 127.0.0.1:3306`

代表 MySQL 沒有啟動。

解決方法：

1. 打開 XAMPP Control Panel
2. 啟動 `MySQL`
3. 確認 phpMyAdmin 可以打開：

```text
http://localhost/phpmyadmin
```

### 6. `ER_ACCESS_DENIED_ERROR`

代表 MySQL 帳號或密碼錯誤。

檢查 `server/.env`：

```env
DB_USER=root
DB_PASSWORD=
```

XAMPP 預設通常沒有密碼，所以 `DB_PASSWORD=` 後面應留空。

### 7. `Unknown database 'mindanchor'`

代表資料庫尚未建立或未匯入。

解決方法：

1. 打開 phpMyAdmin
2. 建立 `mindanchor` 資料庫
3. 匯入 `database/mindanchor.sql`

### 8. `Port 5000 is already in use`

代表 5000 port 已被其他程式使用。

解決方法：

關閉舊的後端 Terminal，或修改 `server/.env`：

```env
PORT=5001
```

然後重新啟動後端。

### 9. `Port 5173 is already in use`

代表 React 前端已在運行。

解決方法：

關閉舊的前端 Terminal，或按 `Ctrl + C` 停止目前程式，再重新執行：

```bash
npm run dev
```

### 10. `git pull` 出現 conflict

代表你和組員修改了同一個檔案。

解決方法：

1. 打開有 conflict 的檔案
2. 尋找以下符號：

```text
<<<<<<< HEAD
=======
>>>>>>>
```

3. 選擇要保留的代碼
4. 刪除 conflict 符號
5. 再執行：

```bash
git add .
git commit -m "Resolve merge conflict"
git push
```

## 不要上傳到 GitHub 的檔案

請確保根目錄有 `.gitignore`：

```text
node_modules/
.env
client/dist/
server/logs/
.DS_Store
```

特別注意：

- `.env` 包含資料庫密碼和 JWT secret，不可以上傳
- `node_modules/` 檔案很大，不需要上傳
- `client/dist/` 是 build 後產生的檔案，不需要上傳

## 常用 Git 指令

| 指令 | 用途 |
|---|---|
| `git status` | 查看哪些檔案被修改 |
| `git pull origin main` | 下載最新代碼 |
| `git checkout -b feature/xxx` | 建立新功能分支 |
| `git add .` | 加入所有修改檔案 |
| `git commit -m "說明"` | 儲存修改紀錄 |
| `git push origin feature/xxx` | 上傳分支到 GitHub |
| `git log` | 查看提交紀錄 |

## 專案啟動檢查清單

開始寫 code 前，確認以下事項：

- [ ] XAMPP 的 Apache 已啟動
- [ ] XAMPP 的 MySQL 已啟動
- [ ] phpMyAdmin 可以打開
- [ ] `mindanchor` 資料庫已建立或匯入
- [ ] `server/.env` 已設定
- [ ] `client/` 已執行 `npm install`
- [ ] `server/` 已執行 `npm install`
- [ ] 後端已啟動：`http://localhost:5000`
- [ ] 前端已啟動：`http://localhost:5173`