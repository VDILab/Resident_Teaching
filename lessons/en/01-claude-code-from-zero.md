# Lesson 1 — From Zero to Using Claude Code

> Course overview: [00-overview.md](00-overview.md).
> **General skill**: terminal / AI collaboration basics (the gateway to all technical work).
> **Goal of this lesson**: within a single session, get the learner to run Claude themselves + complete a first analysis (reading their own de-identified cohort).
> **Format**: hands-on demo; learners follow along.
> **Deliberately not taught** (left for later, to lower the barrier): usage skills / mindset (Lesson 2), the three work-habit files (Lesson 3), git (Lesson 4), full PHI (only a one-line bottom line here). Lesson 1 does only "get it installed + run the first analysis" — no more.

---

## 1-1 Opening — The Terminal vs. the Chat Interface You Know

> Purpose: build a bridge. Learners mentally compare this to the ChatGPT / Claude web app, so first make the difference clear and dispel the fear of "white text on a black screen."

- One-line framing: web chat = a person who can talk; the Claude Code terminal = a person sitting at your computer who can actually do things.
- Five key differences (what you can see / what it can do / how data goes in / where results land / what it looks like) → use a comparison table.
- Practical meaning for research: CSV analysis as "a dozen copy-paste round trips in the web app" vs. "the terminal reads the file and runs it directly" → this is the reason to use the terminal version.
- **Key reassurance**: you don't need to learn commands — just type in your language and talk to it; the terminal is merely where it "lives."

### 📇 Three Words You'll Hear Constantly (a quick glossary)

> No need to memorize or fully understand them — just get familiar; the details come later when you use them.

| Term | Plain meaning | In one line |
|------|---------------|-------------|
| **prompt** | the instruction you give | the message you type to Claude. Type in your own language — that's a prompt, nothing fancy. |
| **session** | one working conversation | one `claude` open-to-close = one session; within it, it remembers what you said — **close it and it forgets** (details in Lesson 2). |
| **context** | the background / what it's tracking | what Claude "currently remembers" — the background you gave, files it read, what you discussed. **The clearer you are, the better it answers** (skills in Lesson 2). |

> ⚠️ One easy mix-up: in 1-2 you'll see the terminal's "**prompt**" `username@mac ~ %` — English calls that a prompt too, but it's just the symbol meaning "the computer is waiting for you to type," **not the same thing as the "instruction you give" above** — the context makes it clear.

---

## 1-2 iTerm2 — Set the Stage First

> Purpose: let them understand what iTerm2 is, install it, and read the first screen.

- What iTerm2 is: a terminal app (a better replacement for macOS's built-in Terminal). **iTerm2 ≠ Claude.**
- Analogy: iTerm2 = the stage, Claude Code = the actor on it; you need the stage before the actor can step up.
- Why iTerm2 over the built-in Terminal: tabs / search / better configuration / smoother to use.
- Install iTerm2: download the .dmg from iterm2.com → drag into Applications (most intuitive for beginners; no need to understand brew first).
- First open: a blank screen + a blinking cursor = normal, don't be alarmed.
- Reading the prompt (`username@mac ~ %`) = "the computer is waiting for you to type."

---

## 1-3 Install Claude Code Through the Terminal

> Purpose: hands-on install of Claude. This is the first command the learner pastes, so **it must be correct**.

**Install (the official Native Install for macOS):**

```sh
curl -fsSL https://claude.ai/install.sh | bash
```

- This installs it and auto-updates in the background afterward — beginners don't need to manage the details.
- (Other methods like Homebrew `brew install --cask claude-code` are for those already familiar; for a first install, the line above is the simplest.)

**Confirm it installed:**

```sh
claude --version    # a version number = success
claude doctor       # a more detailed health check (run this if it won't install)
```

**Launch:** type `claude` and press Enter (details in 1-4).

**⚠️ One prerequisite:** Claude Code requires a paid plan (**Pro / Max / Team**, etc.); the free Claude.ai plan can't use it (log in with your lab / personal seat → see 1-4's `/login`).

**Common snags:**

- `command not found: claude` → the install hasn't taken effect; **quit and reopen iTerm2** (the PATH needs reloading); still failing, run `claude doctor`.
- Requires **macOS 13.0+** and 4GB+ RAM.

> Version note: install methods may change; defer to the [official docs](https://code.claude.com/docs/en/setup) (this course is aligned to 2026-06).

---

## 1-4 Run Claude Inside iTerm2

> Purpose: launch + log in + see the conversation mode.

**1. Launch** — in iTerm2, type:

```sh
claude
```

Press Enter. The first launch walks you through login.

**2. First-time login** — it prompts you to log in; follow the on-screen instructions:

```
/login
```

- A browser opens → log in with your Claude account / the team seat your lab gave you → authorize → return to iTerm2 and you're connected.
- ⚠️ **Known pitfall**: after a team / organization policy change, you must `/login` again for it to take effect → if permissions seem off ("weird / can't use it") after joining a team, **log in again first**.

**3. What it looks like after launch** — the screen enters **Claude's conversation mode** (an input box, prompting you to type) → now just type in your own language and talk to it.

> Quick tip: from now on, each use is just two steps — "`cd` into your folder (1-5) → type `claude`."

---

## 1-5 Let Claude See Your Folder (the Most Critical Section)

> Purpose: dispel the web-app misconception of "loading a folder" and build the correct mental model for Claude Code. This is what learners get stuck on most and should understand first.

- **🔑 Core correction**: Claude Code **has no "load / upload a folder" action**.
  - Web app: you upload / drag files in for it to see them → "loading."
  - Claude Code: it **automatically sees the folder you are currently in** (the working directory). You don't load anything — you `cd` **into** a folder and it stands there with you.
  - **Mental model in one line**: it's not "load the folder into Claude," it's "**you walk into the folder, and Claude stands there with you**." Whichever folder you're standing in is what it can see.
- **Hands-on steps** — three commands, type them in iTerm2 in order:

  ```sh
  cd ~/Desktop/my_research/cohort_analysis   # 1. walk into your research folder
  pwd                                         # 2a. confirm you're in the right place
  ls                                          # 2b. see what files are there
  claude                                      # 3. open Claude; its scope is this folder
  ```

  - (Note: after launching claude you can also ask it to read a specific file; but "cd in first, then launch" is the most intuitive — learn this one first.)
- Giving instructions in your own language = just talk to it (no command syntax to learn).
- Ending (`Ctrl-C` twice or type `exit`) / reopening a session.

### 🎯 First File Read + First Analysis (the Lesson 1 highlight demo)

> ✅ **Use the learner's own real de-identified cohort data** (de-identified via ID codes, not names / medical record numbers → no PHI concern for local analysis). This is the strongest motivation and immediately useful for their own research.

**Demo flow (hands-on; each person runs it once in their own folder)**:

1. Walk into the folder, confirm the file is there, open Claude:

   ```sh
   cd ~/Desktop/my_research/cohort_analysis
   ls            # confirm you can see your cohort file
   claude
   ```

2. Give the first instruction in your language (**type it into the chat box**), e.g.:

   > Read `my_cohort.csv` in this folder and tell me how many rows, how many columns, and the missing count per column.

3. Hit the permission prompt (see 1-6) → teach them to approve → Claude actually reads the file.
4. One step further, type:

   > Do descriptive statistics, and plot the age distribution as a histogram saved as `age_dist.png`.

   → they watch the result get **written to a file** in their own folder (`ls` now shows `age_dist.png`).
5. **Achievement anchor**: their first experience = "the AI read **my own real research data**, did an analysis, and saved a figure" — not a toy example.

- ⚠️ **The one PHI bottom line in Lesson 1** (not expanded; full version in Lesson 4):
  - "**Claude reads files and analyzes locally on your computer; the data isn't sent out = safe**; your cohort is de-identified with ID codes, which is even safer."
  - "But **don't paste full clinical notes / raw records (with names, medical record numbers) into the chat box**. Reading a de-identified file locally is OK; manually pasting PHI into the chat is not."
  - Details (shared Projects, metadata, compliance-environment differences across AI services) → Lesson 4. Lesson 1 only holds this one line.

---

## 1-6 Granting Access — You'll Hit This on the First File Read

> Purpose: the first time a learner asks it to read a file, two gates appear; not understanding them is scary / leads to random clicking. Teach this chapter at the moment of the first task (the prompt appears right then).
> Order of gates: first the macOS system permission (B), then Claude's per-action prompt (A).

### B. macOS System-Level Permission (hit first)

- Scenario: the first time iTerm2 touches a file under `~/Desktop` / `~/Documents` → **macOS pops a system dialog**: "iTerm2 wants to access your Desktop folder."
- ⚠️ Research data often lives under Desktop / Documents → **you'll very likely hit this**. Deny it = Claude can't read the file and keeps failing.
- What to do: click "Allow"; if you missed it → **System Settings → Privacy & Security → Files and Folders (or Full Disk Access) → enable iTerm2**.
- (Teaching tip: before the demo, confirm iTerm2 already has permission to avoid getting stuck live.)

### A. Claude's Per-Action Prompts (when reading / editing files / running commands)

- Scenario: when Claude wants to **read a file / edit a file / run a command**, it shows a prompt asking "allow?"
- Make the three options clear:
  - `Yes` = allow this time
  - `Yes, and don't ask again` = trust this type of action; the same kind of operation in the same folder won't ask each time (convenient, but know what you're allowing)
  - `No` = deny this time
- **This is a safety design, not a malfunction**: Claude asks before touching your files / running commands = you stay in control at all times.
- Learner mindset: understand what it's about to do → `Yes`; unsure → look carefully first, or ask your supervisor.

> 🔗 **On to Lesson 2**: you can now *run* it, but not necessarily *use it well*. How to ask effectively, `/` commands, how to recover from errors, what a session is — all in [Lesson 2: Using Claude Code Well](02-using-claude-well.md).

---

## End of Lesson 1 — What the Learner Takes Away

**Skills**: boot it up independently / understand "cd into a folder = Claude stands there" / pass the permission gates / give instructions in their language.
**State**: iTerm2 + Claude installed and logged in, macOS authorized, knows where their folder is.
**Output**: ran their first Claude analysis (their own real cohort) + saw read → statistics → figure-saved.
**Conceptual foundation**: holds one PHI bottom line.

> In one line: **from "never touched a terminal" to "can analyze my own research data with AI."**
> Lesson 1 does just one thing: **get it installed, run the first analysis.** How to use it well is Lesson 2 — don't overload here.

---

*Status: draft outline. Content to be expanded chapter by chapter.*
