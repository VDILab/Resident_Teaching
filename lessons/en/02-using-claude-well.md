# Lesson 2 — Using Claude Code Well (Skills / Mindset)

> Course overview: [00-overview.md](00-overview.md).
> **General skill**: the fundamentals of collaborating with an AI (how to ask, how to keep control, how to recover).
> **Opening hook** (picking up Lesson 1): "You can already run it. But with the same Claude, some people fly and others keep hitting walls — the difference isn't the tool, it's **how you use it**. That's what today is about."
> **Positioning**: Lesson 1 was "boot it up"; this lesson is "**once it's running, how to use it well**." All everyday, immediately useful tricks — not advanced features.

---

## 2-1 How to Ask Effectively (prompting basics)

> However powerful the tool, a bad question gets a bad answer. This is the highest-ROI section.

- **Bad vs. good ways to ask** (clinical-research scenarios):

  ❌ Bad (too vague — it can only guess):
  > Analyze my data

  ✅ Good (give the filename, what you want, the format):
  > Read `cohort.csv` in this folder; tell me the missing count per column, and the median + IQR of age.

  ❌ Bad:
  > Draw a chart

  ✅ Good:
  > Plot TBSA against length of stay as a scatter plot, add a trend line, save it as `tbsa_los.png`.

- **Three mindsets**:
  1. **Give context**: what your research is about, what this file is, what format you want. The clearer you are, the more accurate the answer.
  2. **One thing at a time**: don't cram five requests into one sentence — split them, easier to follow and to fix.
  3. **Ask it to state a plan first**: for complex tasks, tell it to "**don't act yet — tell me how you plan to do it**," and you review before approving (see 2-3).

---

## 2-2 Handy `/` Commands (slash commands)

> Typing a `/`-prefixed command in the Claude conversation triggers a built-in shortcut. As a beginner, just remember a few of the most-used.

- **`/clear`** = clear the current conversation and start fresh (no need to quit and reopen iTerm2). Best when the conversation gets messy or you switch tasks.
- **`/login`** = log in again (use it when permissions act up, or right after being added to a team).
- Type `/` and a list pops up — no need to memorize; use the ones you understand.

### Advanced: Turn Phrases You Type Often Into Your Own command 🛠️

> The above are Claude's built-ins; you can also **make your own**. This is one step up — **use it once you're comfortable** — but it's handy, so know it exists.

- **Motivation**: 2-1 taught "a good prompt is specific," but some phrases you **retype every time** (e.g. "do descriptive statistics + a per-column missingness table + save the age distribution as png"). Save it as a command and next time `/eda` triggers it in one word — no retyping.
- **How to do it** (just create one file): in your project folder, create `.claude/commands/<name>.md` and write that fixed phrase in it. For example, create `.claude/commands/eda.md`:

  ```markdown
  Read the main cohort CSV in this folder and give me:
  1. number of rows and columns
  2. missing count and proportion per column
  3. median + IQR for continuous variables; frequency tables for categorical
  4. save the age distribution as age_dist.png
  ```

- **Use it**: next time in this project, type `/eda` → Claude runs that phrase, no retyping.
- **Mindset**: **any phrase you type a third time is worth making into a command.** Fixed analysis flows, fixed ways of asking, fixed format requirements — all fair game.
- (You can also have Claude make it for you: "save what I just asked as a slash command called eda" — it creates the file.)

---

## 2-3 Plan Mode — Make It "Say Before It Does" (the safety habit to build)

> Beginners fear most that "it changed my file on its own / ran something I didn't understand." The fix: make it report a plan before acting.

- The mindset in one line: **for complex or file-changing tasks, ask it to state a plan first.** Just type:

  > Don't act yet. First tell me how you plan to do it and which files you'll change; I'll confirm before you start.

- You review the plan → looks right → reply:

  > Looks good, go ahead.

  → looks wrong → correct it on the spot ("skip step 2, do … instead"), saving a whole wrong detour.
- Why it matters: you stay in control at all times, never dragged along; it's also your chance to understand "what is it actually about to do."
- (Advanced: Claude Code has a built-in **plan mode** — press `Shift+Tab` to switch to a "plan only, don't act" mode. Use it once you're comfortable; for now the line above is enough.)

---

## 2-4 Have It Read Files / Literature as Reference

> Clinicians read papers daily — this one really resonates.

- You can hand it **PDFs, papers, example files, someone else's code** to read and base its answer on.
- E.g.: "Read `reference.pdf` and summarize its study design and outcome definitions" / "Following the style of `example.py`, adapt it to read my data."

**Three ways to point it at files (precise → broad):**

1. **Name the file directly with `@`** (most precise, recommended) — type `@` and a file list pops up; pick one and it reads exactly that:

   > Check the outcome definition in @reference.pdf and compare it against @my_protocol.md for any discrepancies.

   Why `@` is good: no full path to type, no reading the wrong file, and it knows exactly which one you mean.

2. **Just name the file and let it find it** — `@` is optional; you can just say "read `cohort.csv` in this folder" and it looks in the current folder.

3. **Have it read the whole project** — when you're not sure where the data is, or you want it to get the big picture, tell it to scan the whole folder:

   > Look over this entire project folder and tell me what data files are here, what each is, and how they relate.

   It will `ls` its way through and explore. Great when you've just taken over a project and want it to "get oriented" first.

- ⚠️ Hold Lesson 1's PHI bottom line: reading a **de-identified** file is OK; don't hand it raw records containing names / medical record numbers (before letting it scan a whole folder, confirm there are no un-de-identified raw files in it).

---

## 2-5 How to Recover When Something Goes Wrong

> The AI being wrong, or red error text, is all normal. Self-rescue = not waiting on your supervisor every time.

- **An error message you don't understand**: just copy the whole thing back into the chat and ask "what does this mean, how do I fix it" — it's good at interpreting its own errors.
- **Wrong answer / not what you wanted**: don't restart — just follow up: "no, I wanted X, you just did Y" — give it more context to correct.
- **Truly stuck** (quota, login, won't install): check the [official docs](https://docs.claude.com/en/docs/claude-code/overview), or ask your supervisor.

---

## 2-6 What a Session Is (why closing forgets, why you should save)

> Only the intuition that "affects how you use it," no token / context-window numbers.

> Remember **session** from the Lesson 1 quick glossary? Here's the detail.

- **One `claude` open-to-close = one session**; within a session Claude remembers what you said earlier (like one continuous conversation).
- **Close it and it forgets**: when the session ends, Claude doesn't remember last time (no memory across days) → save important conclusions yourself.
- **Gets duller / fills up**: stuffing too much into one session (reading many large files, chatting long) makes it slow or forgetful → **start a new session for a new task** (or `/clear`).
- Practical habit (80/20): one research task = one session; let it **write important output to a file** (don't leave it only in the chat); conversation gets weird → `/clear` or a new session.

---

## 2-7 Save Outputs to Files (don't leave them in the chat)

> Conversations vanish; files stay. This is the single most important rule of "using it well."

- Build the habit: analysis results, tidied tables, finished code — have it **write them to files** (`.md` / `.csv` / `.py` / `.png`) saved into your folder.
- Why: ① close the chat and it's gone, a file isn't ② you can pick it up next time ③ you can find it when writing the paper.
- 🔗 **Foreshadowing Lesson 3**: the pain of "close it and it forgets" is solved for good in the next lesson — use CLAUDE.md / PROGRESS.md / TODO.md to **externalize memory into files**, so you won't even have to re-explain your project each time.

---

## End of Lesson 2 — What the Learner Takes Away

- Can ask clearly (give context, one thing at a time, ask it to state a plan first).
- Can use basic `/` commands like `/clear`, and have it read files as reference.
- Can self-rescue from errors (paste the error back, follow up to correct).
- Understands the session "close it and it forgets / save it," and builds the habit of writing outputs to files.

> In one line: **from "can run it" to "uses it smoothly."**

---

*Status: draft outline. Content to be expanded chapter by chapter.*
