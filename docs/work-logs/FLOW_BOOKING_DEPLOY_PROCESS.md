# Flow Booking Deploy Process

## 1. Purpose

這份文件是給你下次更新並發布 Flow Booking 前端時使用的部署指南。

目標是把 Flow Booking 的最新前端畫面發布到這個公開網址：

```text
https://sppfoundry.co/labs/flow-booking/
```

這是一份「可以重複使用」的流程文件。也就是說，每次你在原本的 Flow Booking 前端專案修改完畫面、功能或文字之後，都可以照著這份文件一步一步做，最後把更新發布到正式網站。

這份文件假設你不是技術背景，所以會把每一個小步驟都寫清楚。你不需要一次理解所有技術原理，只要照順序做，並在每一步檢查結果即可。

## 2. Big Picture

Flow Booking 的發布流程可以想成四個部分：

1. 原始前端專案
2. build output，也就是建置後產生的網站檔案
3. `sppfoundry-landing` 這個網站倉庫
4. Cloudflare Pages，自動把 GitHub 上的網站發布到正式網址

### Original Frontend Project

「原始前端專案」是你真正開發 Flow Booking 的地方。

你會在這裡修改原始碼，例如：

- 修改頁面文字
- 修改 UI 樣式
- 修改互動功能
- 修改圖片或元件

這個資料夾通常會有像這些檔案或資料夾：

```text
package.json
src/
public/
vite.config.js
```

實際名稱可能依專案而不同，但重點是：這裡是「開發用」的專案，不是直接給正式網站使用的資料夾。

### Build Output

前端專案修改完成後，需要執行 build。

build 的意思是：把開發用的原始碼整理、打包、壓縮，變成瀏覽器可以直接載入的正式網站檔案。

常見的 build output 資料夾名稱是：

```text
dist/
```

也可能是：

```text
build/
```

如果你的專案是 Vite，通常會是 `dist/`。

### sppfoundry-landing Repo

`sppfoundry-landing` 是正式網站內容所在的倉庫。

這個資料夾位置是：

```text
/Users/huapeichang/sppfoundry-landing
```

公開網站 `sppfoundry.co` 是從這個倉庫發布出去的。

很重要：正式公開網址不是直接從原始 Flow Booking 前端專案發布，而是從 `sppfoundry-landing` 裡面的檔案發布。

所以 Flow Booking 最後要放進這個資料夾：

```text
/Users/huapeichang/sppfoundry-landing/labs/flow-booking/
```

### Cloudflare Pages

Cloudflare Pages 會連接到 GitHub 上的 `sppfoundry-landing` repo。

當你把更新 push 到 GitHub 的 `main` 分支後，Cloudflare Pages 會偵測到新的 commit，然後自動重新部署網站。

流程簡化如下：

```text
原始 Flow Booking 前端專案
-> 執行 build
-> 產生 dist/ 或 build/
-> 複製正式檔案到 sppfoundry-landing/labs/flow-booking/
-> git commit
-> git push origin main
-> Cloudflare Pages 自動部署
-> https://sppfoundry.co/labs/flow-booking/ 更新完成
```

## 3. Folder / Repo Assumptions

這份文件會用兩個主要資料夾：

### Original Frontend Project Folder

這是 Flow Booking 原始前端專案所在的資料夾。

你會在這裡做開發和 build。

因為不同時間專案資料夾名稱可能不一樣，請你以實際專案位置為準。你可以用 Finder 找到那個專案資料夾，通常裡面會有：

```text
package.json
src/
public/
```

在這份文件中，我們會用這個名稱代表它：

```text
原始 Flow Booking 前端專案資料夾
```

請不要把這個資料夾和 `sppfoundry-landing` 混在一起。

### sppfoundry-landing Folder

這是正式網站倉庫所在的資料夾：

```text
/Users/huapeichang/sppfoundry-landing
```

你目前這份文件也會被放在這裡：

```text
/Users/huapeichang/sppfoundry-landing/working-logs/FLOW_BOOKING_DEPLOY_PROCESS.md
```

### Final Published Files Folder

Flow Booking 最後要發布的正式檔案，需要放在：

```text
/Users/huapeichang/sppfoundry-landing/labs/flow-booking/
```

這個資料夾的內容會對應到正式網址：

```text
https://sppfoundry.co/labs/flow-booking/
```

請記住：

- 原始前端專案是拿來開發和 build 的
- `dist/` 或 `build/` 是 build 後產生的正式網站檔案
- `sppfoundry-landing/labs/flow-booking/` 是正式網站實際會發布的資料夾

## 4. How to Open Terminal

Terminal 是 Mac 上用文字指令操作電腦的工具。

你可以用以下幾種方式打開 Terminal。

### Method A: Use Spotlight Search

1. 按鍵盤上的 `Command + Space`
2. 螢幕中間會出現搜尋框
3. 輸入：

```text
Terminal
```

4. 按 `Enter`
5. Terminal 視窗會打開

### Method B: Open Terminal from Applications

1. 打開 Finder
2. 點左側的 `Applications`
3. 找到 `Utilities`
4. 打開 `Utilities`
5. 找到 `Terminal`
6. 連點兩下打開

### Method C: Open Folder First, Then Use Terminal

如果你先用 Finder 打開某個資料夾，也可以再開 Terminal，然後用 `cd` 指令進到那個資料夾。

例如你在 Finder 看到：

```text
/Users/huapeichang/sppfoundry-landing
```

打開 Terminal 後，需要輸入：

```bash
cd /Users/huapeichang/sppfoundry-landing
```

然後按 `Enter`。

### What "Go Into a Folder" Means

在 Terminal 裡，「進到某個資料夾」的意思是：讓 Terminal 接下來的指令都在那個資料夾裡執行。

就像你在 Finder 裡雙擊資料夾打開它一樣。

Terminal 裡使用的是 `cd` 指令。

## 5. How to Move Into a Folder in Terminal

### Use `cd`

`cd` 的意思是 change directory，也就是「切換資料夾」。

例如要進到 `sppfoundry-landing`：

```bash
cd ~/sppfoundry-landing
```

或使用完整路徑：

```bash
cd /Users/huapeichang/sppfoundry-landing
```

兩個方式通常都可以。

`~` 代表你的使用者家目錄，也就是：

```text
/Users/huapeichang
```

所以：

```bash
cd ~/sppfoundry-landing
```

等於：

```bash
cd /Users/huapeichang/sppfoundry-landing
```

### Confirm Current Location with `pwd`

進到資料夾後，可以用 `pwd` 確認你現在在哪裡。

輸入：

```bash
pwd
```

如果你在 `sppfoundry-landing`，應該會看到：

```text
/Users/huapeichang/sppfoundry-landing
```

### List Files with `ls`

你可以用 `ls` 看目前資料夾裡有哪些檔案。

輸入：

```bash
ls
```

如果你在 `sppfoundry-landing`，可能會看到類似：

```text
index.html
labs
working-logs
```

看到 `index.html`、`labs`、`working-logs` 這些項目，就代表你應該在正確的資料夾。

## 6. Full Deployment Steps

這一段是完整部署流程。請照順序做，不要跳步。

在執行任何指令之前，請先確認你現在是在正確的資料夾。每次不確定時，都先輸入：

```bash
pwd
```

再輸入：

```bash
ls
```

`pwd` 會告訴你目前所在位置，`ls` 會列出目前資料夾裡的檔案。這兩個指令可以幫你避免在錯誤的資料夾 build、copy 或操作 Git。

### Step 1: Finish Changes in the Original Frontend Project

先到原始 Flow Booking 前端專案。

這是你開發 Flow Booking 的地方，不是 `sppfoundry-landing/labs/flow-booking/`。

在這個原始專案裡完成所有修改，例如：

- 修改頁面文字
- 修改樣式
- 修改功能
- 修改圖片
- 修正錯誤

完成後，最好先在本機預覽一次，確認畫面和功能是你想要的。

如果專案有開發伺服器，常見指令可能是：

```bash
npm run dev
```

實際指令請以原始前端專案的 `package.json` 為準。

### Step 2: Build the Original Frontend Project

在原始 Flow Booking 前端專案資料夾裡，執行 build。

常見指令是：

```bash
npm run build
```

請注意：這個指令要在「原始前端專案」裡執行，不是在 `sppfoundry-landing` 裡執行。

如果 build 成功，Terminal 通常會顯示完成訊息，並產生一個 build output 資料夾。

常見資料夾名稱是：

```text
dist/
```

如果你的專案不是 Vite，也可能是：

```text
build/
```

### Step 3: Find the Build Output

build 完成後，在原始前端專案裡找 build output。

先輸入：

```bash
ls
```

看看有沒有：

```text
dist
```

或：

```text
build
```

如果看到 `dist/`，通常正式網站檔案就在裡面。

你可以再看一次：

```bash
ls dist
```

你應該會看到類似：

```text
index.html
assets
```

這些才是要放到 `sppfoundry-landing/labs/flow-booking/` 的正式檔案。

### Step 4: Copy Built Files Into sppfoundry-landing

接下來要把 build output 裡面的檔案，複製到：

```text
/Users/huapeichang/sppfoundry-landing/labs/flow-booking/
```

如果 build output 是 `dist/`，你要複製的是 `dist/` 裡面的內容，不是整個原始專案。

很重要：

- 要複製 `dist/` 裡面的檔案
- 不要複製原始專案的 `src/`
- 不要複製整個原始專案
- 不要把 `package.json` 當成正式網站檔案複製過去

可以用 Finder 手動做：

1. 在 Finder 打開原始 Flow Booking 前端專案
2. 打開 `dist/`
3. 選取 `dist/` 裡面的所有內容
4. 複製
5. 打開：

```text
/Users/huapeichang/sppfoundry-landing/labs/flow-booking/
```

6. 比較安全的做法是：先刪除這個資料夾裡舊的已發布檔案
7. 再把新的 `dist/` 內容貼上或複製進來

這樣可以避免舊版本留下來的檔案沒有被覆蓋到，造成網站載入到過期的 assets。

你也可以用 Terminal 做，但如果你不熟指令，建議先用 Finder，因為比較直覺。

### Step 5: Update Landing Page Entry If Needed

如果這次只是更新 Flow Booking 裡面的內容，通常不需要修改 landing page。

但如果你有改到 `sppfoundry.co` 首頁上的入口，例如：

- 首頁連到 Flow Booking 的按鈕文字
- 首頁連結位置
- 首頁卡片標題
- 首頁 Flow Booking 介紹文字

那才需要編輯：

```text
/Users/huapeichang/sppfoundry-landing/index.html
```

如果你只是重新發布 Flow Booking 本身，通常只要更新：

```text
/Users/huapeichang/sppfoundry-landing/labs/flow-booking/
```

### Step 6: Move Into sppfoundry-landing

現在要到 `sppfoundry-landing` repo 裡面準備提交。

在 Terminal 輸入：

```bash
cd /Users/huapeichang/sppfoundry-landing
```

確認位置：

```bash
pwd
```

應該看到：

```text
/Users/huapeichang/sppfoundry-landing
```

### Step 7: Run `git status`

在 `sppfoundry-landing` 裡，輸入：

```bash
git status
```

這會告訴你有哪些檔案被修改、新增或刪除。

你應該會看到 `labs/flow-booking/` 裡面有變更。

如果你也有修改首頁入口，可能會看到：

```text
index.html
```

請確認變更的檔案是你預期的。

如果看到完全不認識的檔案，不要急著 commit。先停下來確認那些檔案是不是應該被發布。

### Step 8: Run `git add`

如果確認變更正確，就把這些變更加入準備提交的清單。

如果你只要加入 Flow Booking：

```bash
git add labs/flow-booking/
```

如果你也有修改首頁：

```bash
git add labs/flow-booking/ index.html
```

如果你非常確定所有變更都要一起發布，也可以用：

```bash
git add .
```

但初學者比較建議用明確的路徑，例如：

```bash
git add labs/flow-booking/
```

這樣比較不容易把不相關的檔案一起加進去。

### Step 9: Run `git commit`

加入變更後，建立 commit。

commit 可以想成「把這次修改打包成一個有名字的版本」。

輸入：

```bash
git commit -m "Update Flow Booking frontend"
```

如果這次有更明確的內容，也可以寫得更清楚，例如：

```bash
git commit -m "Update Flow Booking landing copy and assets"
```

commit 訊息不需要很長，但要讓未來的你看得懂這次做了什麼。

### Step 10: Push to GitHub

commit 完成後，把更新推到 GitHub 的 `main` 分支。

輸入：

```bash
git push origin main
```

這一步完成後，GitHub 上的 `sppfoundry-landing` repo 就會有最新版本。

Cloudflare Pages 會偵測到這次 push，然後開始重新部署網站。

### Step 11: Check Cloudflare Pages Deployment

打開 Cloudflare Dashboard。

找到 Pages 專案，通常名稱會和 `sppfoundry-landing` 有關。

進入該 Pages 專案後，找部署紀錄，通常會看到最新一次 deployment。

你要確認：

- 最新 deployment 有開始
- 最新 deployment 對應到你剛剛 push 的 commit
- 狀態最後變成成功，例如 `Success`

如果還在跑，等幾分鐘再刷新頁面。

### Step 12: Verify the Live Site

Cloudflare 顯示成功後，打開正式網址：

```text
https://sppfoundry.co/labs/flow-booking/
```

檢查：

- 頁面是否打得開
- 畫面是否是最新版本
- 按鈕是否可以按
- 表單或互動功能是否正常
- 手機尺寸看起來是否正常
- 桌機尺寸看起來是否正常

如果首頁也有入口，請打開：

```text
https://sppfoundry.co/
```

然後點 Flow Booking 的入口，確認會進到：

```text
https://sppfoundry.co/labs/flow-booking/
```

## 7. Git Commands Explained

### `git status`

```bash
git status
```

意思是：查看目前有哪些檔案被修改、新增或刪除。

你可以把它想成「檢查目前工作區狀態」。

每次 commit 前都建議先跑一次。

### `git add`

```bash
git add labs/flow-booking/
```

意思是：告訴 Git，這些變更我要放進下一次 commit。

`git add` 不會發布網站，也不會上傳 GitHub。

它只是把檔案放進「準備提交」的清單。

### `git commit -m`

```bash
git commit -m "Update Flow Booking frontend"
```

意思是：建立一個新的版本紀錄。

`-m` 後面的文字是這次 commit 的說明。

commit 完成後，變更已經被記錄在你的本機 Git 裡，但還沒有上傳到 GitHub。

### `git push origin main`

```bash
git push origin main
```

意思是：把你本機的 commit 上傳到 GitHub 的 `main` 分支。

這一步通常會觸發 Cloudflare Pages 自動部署。

也就是說：

```text
git commit = 在你的電腦建立版本
git push = 把版本送到 GitHub，讓 Cloudflare 可以發布
```

## 8. Cloudflare Check

部署後要到 Cloudflare Pages 確認，不要只看 Terminal。

### Where to Look

1. 打開 Cloudflare Dashboard
2. 進入 Pages
3. 找到 `sppfoundry-landing` 對應的 Pages project
4. 打開部署列表
5. 找最新的一筆 deployment

### How to Confirm Deployment Succeeded

確認以下幾件事：

- 最新 deployment 的時間是在你剛剛 push 之後
- deployment 對應的 commit 訊息是你剛剛寫的那個
- 狀態是成功，例如 `Success`
- 沒有紅色錯誤訊息

如果 deployment 失敗：

1. 點進失敗的 deployment
2. 查看錯誤訊息
3. 不要重複亂 push
4. 先確認是 build 設定、檔案路徑，還是 GitHub 內容有問題

如果你不確定錯誤代表什麼，先把錯誤訊息複製下來，再請人協助判斷。

## 9. Final Verification Checklist

Cloudflare Pages 成功後，請做最後檢查。

### Direct Project URL

打開：

```text
https://sppfoundry.co/labs/flow-booking/
```

確認：

- 網站可以正常載入
- 沒有 404
- 沒有空白頁
- 沒有明顯破版
- 內容是最新版本

### Landing Page Link

打開：

```text
https://sppfoundry.co/
```

檢查首頁上的 Flow Booking 入口。

確認：

- 入口文字正確
- 連結可以點
- 點下去會進到 `/labs/flow-booking/`
- 不會連到舊網址或錯誤頁面

即使首頁連結可以正常點開，也請另外直接打開這個網址：

```text
https://sppfoundry.co/labs/flow-booking/
```

確認 Flow Booking 實際頁面內容是最新版本，不要只依賴首頁連結是否正常。

### Visuals and Functionality

請至少檢查：

- 桌機畫面
- 手機畫面
- 主要按鈕
- 表單或選項
- 圖片是否載入
- 文字是否正確
- 頁面是否有奇怪的空白或重疊

如果有改功能，請實際操作一次，不要只看畫面。

## 10. Common Mistakes

### Forgetting to Build

最常見錯誤是：在原始前端專案改完後，忘記執行：

```bash
npm run build
```

如果沒有 build，你複製到 `sppfoundry-landing` 的可能還是舊版本。

### Copying the Wrong Folder

請確認你複製的是 build output 裡面的內容。

通常是：

```text
dist/
```

不要複製整個原始專案。

### Copying Source Code Instead of Build Output

不要把這些原始開發檔案當成正式網站檔案複製過去：

```text
src/
package.json
vite.config.js
node_modules/
```

正式網站通常需要的是：

```text
index.html
assets/
```

這些通常會出現在 `dist/` 裡。

### Forgetting `git add`

如果你忘記 `git add`，commit 可能不會包含你的檔案。

請先跑：

```bash
git status
```

再用：

```bash
git add labs/flow-booking/
```

### Forgetting `git commit`

如果只有 `git add`，但沒有 `git commit`，變更還沒有變成正式版本紀錄。

需要執行：

```bash
git commit -m "Update Flow Booking frontend"
```

### Forgetting `git push`

如果你有 commit，但忘記 push，GitHub 和 Cloudflare 都不會收到更新。

需要執行：

```bash
git push origin main
```

### Cloudflare Not Updated Yet

push 完不是網站立刻更新。

Cloudflare Pages 需要一點時間部署。

請到 Cloudflare Pages 看最新 deployment 是否完成。

如果還在部署中，等幾分鐘再檢查正式網址。

### Browser Cache Confusion

有時候網站其實已經更新，但瀏覽器還顯示舊版本。

你可以試試：

- 按 `Command + Shift + R` 強制重新整理
- 用無痕視窗打開網站
- 換另一個瀏覽器查看
- 在手機上用行動網路測試

如果無痕視窗看到新版本，代表很可能只是瀏覽器快取問題。

## Real Example Used in This Project

這個專案目前實際使用的發布目標是：

```text
https://sppfoundry.co/labs/flow-booking/
```

目前的 landing repo 是：

```text
/Users/huapeichang/sppfoundry-landing
```

目前 Flow Booking 在 landing repo 裡的發布資料夾是：

```text
/Users/huapeichang/sppfoundry-landing/labs/flow-booking/
```

請記得：你要在原始 Flow Booking 前端專案裡編輯和 build。build 完成後，再用新的 build output 取代 `sppfoundry-landing` 裡 `labs/flow-booking/` 的內容。最後要回到 `sppfoundry-landing` 裡執行 git commit 和 git push，Cloudflare Pages 才會收到更新並發布到正式網站。

## 11. Short Version

### Quick Deploy Checklist

1. 在原始 Flow Booking 前端專案完成修改
2. 在原始前端專案執行：

```bash
npm run build
```

3. 找到 build output，通常是：

```text
dist/
```

4. 把 `dist/` 裡面的內容複製到：

```text
/Users/huapeichang/sppfoundry-landing/labs/flow-booking/
```

5. 如果首頁入口也需要更新，才修改：

```text
/Users/huapeichang/sppfoundry-landing/index.html
```

6. 進到 `sppfoundry-landing`：

```bash
cd /Users/huapeichang/sppfoundry-landing
```

7. 檢查變更：

```bash
git status
```

8. 加入 Flow Booking 變更：

```bash
git add labs/flow-booking/
```

9. 如果有改首頁，也加入首頁：

```bash
git add index.html
```

10. 建立 commit：

```bash
git commit -m "Update Flow Booking frontend"
```

11. 推到 GitHub：

```bash
git push origin main
```

12. 到 Cloudflare Pages 檢查 deployment 是否成功
13. 打開正式網址確認：

```text
https://sppfoundry.co/labs/flow-booking/
```

14. 從首頁點 Flow Booking 入口，確認連結也正常
