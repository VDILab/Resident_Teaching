# Developer Literacy for Clinical Researchers — Course Overview

> Audience: clinicians / residents / research assistants from a clinical, non-engineering background who have never used a terminal.
> Platform assumption: macOS + the terminal (CLI) version of Claude Code (terminal app: iTerm2).
> Status: 🚧 Draft outline (work-in-progress). Each lesson is a teaching outline; content is being expanded chapter by chapter.

---

## Core Philosophy

**Use "doing research" as the practice field, but teach "general technical skills you keep for life."**

This is not merely "teaching you to run your own cohort" — it is cultivating a **clinical researcher who is fluent with modern tools**. Research is the immediate lever; the skill is the long-term investment. Every tool has two layers:

| Tool | General skill (lifelong) | Research payoff (immediate) |
|------|--------------------------|------------------------------|
| Terminal / iTerm2 | Gateway to all technical work | Run your own analysis |
| Claude Code | AI-assisted development | Read cohorts, run statistics |
| CLAUDE.md / PROGRESS / TODO | Project management / knowledge externalization | Manage your own paper's progress |
| git / GitHub | Version control / collaboration / cloud backup (lifelong skill) | Back up code, collaborate with a team |

- **Format**: hands-on demo; learners follow along and each runs it once on their own project.
- **Platform assumption**: macOS + the terminal (CLI) version (not the desktop app); terminal app is **iTerm2**.

---

## Course Map

| # | File | Topic | General skill | Takeaway |
|---|------|-------|---------------|----------|
| **Lesson 1** | [01-claude-code-from-zero.md](01-claude-code-from-zero.md) | From zero to using Claude Code | Terminal / AI collaboration basics | Get it installed, read your own de-identified cohort, produce a first analysis + figure |
| **Lesson 2** | [02-using-claude-well.md](02-using-claude-well.md) | Using Claude Code well (skills / mindset) | Fundamentals of collaborating with an AI | Can ask well, use `/` commands, self-rescue, save outputs |
| **Lesson 3** | [03-knowledge-externalization.md](03-knowledge-externalization.md) | Work habits = knowledge externalization ⭐ | Project management / documentation method | Each project has a CLAUDE.md; maintain PROGRESS / TODO |
| **Lesson 4** | [04-git-and-phi.md](04-git-and-phi.md) | git / GitHub + data compliance (PHI) | Version control / collaboration / backup + data compliance | Can commit / push, understand versioning and backup, understand PHI rules |

> Ordering logic: first **get it installed and running** (Lesson 1) → then **use it well** (Lesson 2, skills) → then **use it systematically** (Lesson 3, documentation habits) → then **use it safely and collaboratively / reproducibly** (Lesson 4, git + PHI). git carries the heaviest conceptual load, so it comes last; the full data-compliance discussion rides along with git (pushing to the cloud is exactly when it matters most).

---

## Advanced Topics (planned)

The first four lessons focus on going "from zero to systematic — **on your own machine**." When learners need to step beyond the local machine and use remote compute, an advanced lesson will be added. **Not yet written — roadmap only**:

| # | Topic | General skill | Status |
|---|-------|---------------|--------|
| **Lesson 5** | Remote-server compute (SSH + tmux + file transfer) | Connect to a remote GPU server; use `tmux` to keep long-running jobs alive in the background / reattach after a disconnect | 🗓️ planned |

> Teaching rationale: on your own machine, iTerm2 tabs are enough. `tmux` earns its keep when you "SSH into a remote server to run training and the job keeps running after you close your laptop" — so it's deferred until learners actually need remote compute.

---

## An Important Premise: De-identification and Data Compliance

This course always demonstrates with **de-identified data** (ID codes in place of names / medical record numbers). Clinical research data involves patient privacy. Before using any AI tool, make sure:

- Reading a de-identified file locally for analysis = data stays on your computer, relatively safe.
- **Do not** paste raw clinical notes containing names / medical record numbers into the chat box.
- Each institution has its own IRB / data-governance rules; defer to your own institution's policy.

Full discussion in [Lesson 4](04-git-and-phi.md).

---

*Status: draft outline. Each lesson is a teaching outline; content to be expanded chapter by chapter.*
