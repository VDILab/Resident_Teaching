# Resident Teaching — Developer Literacy for Clinical Researchers

> 給臨床研究者的開發工具素養 — 一套手把手課程
> Maintained by **VDI Lab** (Vascular & Digital Imaging Lab), Chang Gung Memorial Hospital Burn Center.
> 🚧 **Status: work-in-progress draft.** Lessons are teaching outlines being expanded chapter by chapter. Content and structure may change.

---

## 這是什麼 / What This Is

A hands-on curriculum that takes a clinician with **zero terminal experience** to **analyzing their own research data with AI** — and teaches general, lifelong technical skills along the way. Lessons are added over time.

一套手把手的課程：把**完全沒碰過終端機**的臨床醫師，帶到**能用 AI 分析自己的研究資料**，過程中教的是一輩子帶得走的通用 technical 能力。課程會陸續增加。

**核心哲學 / Core philosophy**: use "doing research" as the practice field, but teach skills you keep for life.
用「做研究」當練習場，教的卻是「一輩子帶得走的通用能力」。

**Audience / 對象**: clinicians, residents, and research assistants from a clinical (non-engineering) background. Platform: macOS + terminal Claude Code (terminal app: iTerm2).
臨床、非工程背景的醫師 / 住院醫師 / 研究助理。平台：macOS + 終端機版 Claude Code（介面工具 iTerm2）。

---

## 課程列表 / Lessons

| # | 主題 / Topic | 繁中 | English |
|---|--------------|------|---------|
| — | 總覽 / Overview | [zh](lessons/zh/00-overview.md) | [en](lessons/en/00-overview.md) |
| 1 | 從零到會用 Claude Code / From zero to using Claude Code | [zh](lessons/zh/01-claude-code-from-zero.md) | [en](lessons/en/01-claude-code-from-zero.md) |
| 2 | 怎麼用 Claude Code 用得好（技巧）/ Using Claude Code well (skills) | [zh](lessons/zh/02-using-claude-well.md) | [en](lessons/en/02-using-claude-well.md) |
| 3 | 工作習慣 = 知識外部化 / Work habits = knowledge externalization | [zh](lessons/zh/03-knowledge-externalization.md) | [en](lessons/en/03-knowledge-externalization.md) |
| 4 | git / GitHub + 資料合規 (PHI) / git / GitHub + data compliance | [zh](lessons/zh/04-git-and-phi.md) | [en](lessons/en/04-git-and-phi.md) |
| 5 | 遠端伺服器運算 (SSH + tmux) / Remote-server compute | 🗓️ planned | 🗓️ planned |

排序邏輯 / Ordering: 先**會跑** → 再**用得好** → 再**用得有系統** → 再**用得安全且可協作**，之後再跨出本機。
First *get it running* → then *use it well* → then *use it systematically* → then *use it safely and collaboratively*, then beyond the local machine.

---

## ⚠️ 資料合規 / Data Compliance

All examples use **de-identified data** (ID codes, never names or medical record numbers). Clinical research data involves patient privacy — defer to your own institution's IRB and data-governance rules. See [Lesson 4](lessons/en/04-git-and-phi.md) for the full discussion.

所有示範一律使用**去識別化資料**（ID code，絕不用姓名或病歷號）。臨床研究資料涉及病患隱私，以你所屬機構的 IRB / 資料治理規範為準。完整討論見[第四堂](lessons/zh/04-git-and-phi.md)。

---

## 授權 / License

Licensed under [CC BY 4.0](LICENSE). You may share and adapt the material for any purpose, including commercially, as long as you give appropriate credit.
本教材採用 [CC BY 4.0](LICENSE) 授權。你可自由分享與改作（含商業用途），只要適當標示出處。
