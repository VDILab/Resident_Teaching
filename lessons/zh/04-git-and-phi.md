# 第四堂課 — git / GitHub + 資料合規（PHI）

> 課程總覽見 [00-overview.md](00-overview.md)。
> **通用能力**：版本控制 / 協作 / 雲端備份（終身技能，跨專案跨職涯）。
> 壓軸理由：git 概念負擔最重（repo / commit / push / 版本）；且 push 上雲正是講完整資料合規的最佳時機。

---

## 4-1 git 用「通用框架」教，不綁研究

- `commit` = 存檔點 / 時光機（任何專案回到過去任一版）。
- `push` / `pull` = 雲端備份 + 多機 / 多人同步。
- **GitHub** = 作品集 + 協作平台（以後 side project、學習專案都用得到）。
- 深度定位：**極簡通用版**（commit + push + pull + 為什麼），**不教** branch / merge / PR（對非工程背景過重，日後需要再說）。

---

## 4-2 先有 GitHub 帳號 + 第一次登入認證

> 你要 push，得先「有個雲端的家」+「證明你是你」。零基礎學員常卡在這一步——明明會打 git 指令，卻在第一次 push 撞認證牆。這章把它走順。

### 1. 建立自己的 GitHub 帳號

- 為什麼需要：GitHub = 你的 repo 住的雲端；沒帳號就無處可 push。
- 流程：到 [github.com](https://github.com) 註冊 → 選 **Free 方案**（個人學習 / public repo 無限，$0 足夠）。
- 帳號名建議用好認、專業一點的（以後是你的作品集網址，例 `github.com/你的帳號`）。

### 2. 第一次 push 會撞「認證牆」——用 `gh auth login` 過關

- ⚠️ **關鍵坑**：GitHub 早已**不能用密碼 push**。第一次 push 會跳出要求認證，不懂會卡死在這。
- 對零基礎學員，**最不痛的路 = GitHub CLI 的 `gh auth login`**（互動式登入，跟著問答按就好；不用手動弄 token / SSH key 那些重的東西）。

**手把手：**

1. 先裝 GitHub CLI（這是你第一次碰 **Homebrew**——macOS 的套件管理工具，通用技能，值得學）：
   ```sh
   # 若還沒裝 Homebrew，先到 brew.sh 照官方一行指令安裝
   brew install gh
   ```
2. 互動式登入：
   ```sh
   gh auth login
   ```
   跟著問答選：`GitHub.com` → `HTTPS` → 用瀏覽器登入 → 貼上畫面給的一次性代碼 → 完成。
3. 之後 `git push` 就不會再問你密碼 / token —— 認證一次到位。

> 心智模型：`gh auth login` = 「在這台電腦上跟 GitHub 報到一次」，報到完這台電腦就被信任，往後 push 暢通。

---

## 4-3 🔴 核心規則：什麼進 git、什麼不進

> 這條當 git 課的**核心規則**教，不只是註腳 —— 是「什麼該進版本控制」的通用觀念，對研究者很有教育價值。

| 進 git ✅ | 不進 git ❌ |
|----------|-----------|
| 程式碼（`.py` / `.R` / `.ipynb`）| **去識別 cohort 資料（CSV / 任何資料檔）** |
| 文件（CLAUDE.md / PROGRESS / TODO / README）| 大型輸出（模型權重 / 影像 / 中介檔）|
| 設定檔 | 含任何 ID 的東西 |

- **規則一句話**：**git 放「怎麼做的」（code + 文件），不放「資料本身」。** 資料留本地 / 機構儲存，另管。
- 為什麼：
  1. 即使去識別，cohort 上雲仍有合規 / IRB 顧慮。
  2. 資料檔大、變動頻繁，git 不適合。
  3. 研究資料預設不進 git，是普遍的最佳實踐。
- 操作上靠 `.gitignore` 把資料排除（下一章展開）。

---

## 4-4 `.gitignore` — 把上面的政策落地成一個檔

> 政策（什麼不進 git）→ 操作（怎麼真的擋住）。`.gitignore` 就是一張「請 git 忽略這些」的清單，放在專案根目錄。

### 臨床研究者的起手式範本

直接複製這份當基底，每行都在擋一類東西：

```gitignore
# --- 資料絕不進 git（核心規則）---
*.csv
*.xlsx
*.sas7bdat
*.dta
data/
cohort/

# --- 系統 / 編輯器雜訊 ---
.DS_Store
.vscode/

# --- Python ---
__pycache__/
*.pyc
.ipynb_checkpoints/
.env
```

- `*.csv` / `*.sas7bdat` 等 = 用副檔名擋掉所有資料檔（無論放哪）。
- `data/` / `cohort/` = 整個資料夾排除（你習慣把資料放這兩個夾就一勞永逸）。
- `.DS_Store` / `__pycache__/` = 系統 / 程式自動產生的雜訊，不該進版本控制。
- `.env` = 放密碼 / 金鑰的檔，**絕不能上雲**。

### ⚠️ 最常見的陷阱：「我加了 `.gitignore` 怎麼還在？」

- **關鍵觀念**：`.gitignore` **只擋「還沒被 git 追蹤過的檔」**。一個檔若**已經 commit 過**，事後才加進 `.gitignore` 是擋不掉的。
- 要把已追蹤的檔移出：先 `git rm --cached <檔名>`（從 git 移除但保留本機檔），再 commit。
- **最省事心法**：**先建好 `.gitignore`，再 `git add`** —— 順序對就永遠不會中招。新專案第一件事就是放好 `.gitignore`。

---

## 4-5 資料合規（PHI）— 第一堂只給底線，這裡展開

- push 上 GitHub = 公開 / 半公開雲端，所以「資料不進 git」這條同時是版本控制最佳實踐 + 隱私防線。
- 要點：
  - **去識別才進**：任何上雲（git / 雲端硬碟 / AI 對話）的資料都應先去識別。
  - **注意照片 metadata**：醫療照片的 EXIF 可能含拍攝日期 / 裝置 / 位置等可識別資訊。
  - **AI 服務的合規環境差異**：不同 AI 訂閱方案的資料處理條款不同；一般消費級方案**不等於** BAA（HIPAA Business Associate Agreement）環境。涉及 PHI 前，確認你用的工具與機構規範相容。
  - 以你所屬機構的 IRB / 資料治理規範為最終依據。

---

## 4-6 加入 lab 的 GitHub 組織（VDI Lab）

> 你在 4-2 建好了自己的 GitHub 帳號。最後一步：把這個帳號加進 lab 的組織，這樣才看得到 lab 的共用 repo（教材、共用工具、團隊專案）。
> **本節只到「成功加入、看得到 lab repo」為止** —— 真正的協作操作（怎麼把改動推回共用 repo）牽涉 branch / pull request，超出本堂極簡版範圍，等你實際要協作時再教。

- **什麼是 GitHub 組織（Organization）**：一個把多人 repo 收在一起的團隊空間。VDI Lab 的組織是 [`github.com/VDILab`](https://github.com/VDILab)。加入後，lab 的共用 repo 會出現在你帳號可見的清單裡。

**加入流程（三步，跟著做）：**

1. **把你的 GitHub 帳號名給指導者** —— 就是你在 4-2 註冊的那個 username（你 profile 網址 `github.com/你的帳號` 最後那段）。
2. **指導者發邀請** —— lab 的 owner 會從組織後台把你加進來，邀請寄到你註冊 GitHub 的 email。
3. **收信 → 接受邀請（Accept）** —— 點信裡的連結（或到 [github.com/VDILab](https://github.com/VDILab) 頁面頂端的接受橫幅）按 **Accept invitation**。

**確認加入成功：**

- 到 [github.com/VDILab](https://github.com/VDILab)，若你已是成員，看得到組織底下的 repo 清單（例如公開教材 repo）。
- 或在你自己的 GitHub 首頁左上角切換帳號 / 組織的選單裡，會出現 **VDILab**。

> ⚠️ 守 4-3 / 4-5 的紅線不變：**加入 org ≠ 可以把資料推上去**。lab repo 一樣只放 code + 文件，去識別資料與 PHI 永遠不進任何 repo（不分個人 / 組織）。

---

## 第四堂結束 — 學員帶走什麼

- 會 commit / push / pull，懂版本與雲端備份。
- 會用 `.gitignore` 把資料排除、懂「code 進 git、資料不進」。
- 懂 PHI 與資料合規的基本紅線。
- 帳號已加入 lab 的 GitHub 組織（VDILab），看得到共用 repo。

---

## 待定

- [x] ✅ git 教學走 GitHub（建帳號 + `gh auth login`），不純本地起步。
- [ ] PHI 完整版併第四堂 / 或獨立堂（看第四堂份量）。
- [x] ✅ 加「加入 lab GitHub Org」進第四堂（4-6，只到加入 + 看得到 repo；協作操作 branch/PR 另議）。

---

*狀態：大綱草稿。內容待逐章展開。*
