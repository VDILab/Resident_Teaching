# Lesson 3 — Work Habits = Knowledge Externalization ⭐

> Course overview: [00-overview.md](00-overview.md).
> **General skill**: project management / documentation method (portable; useful in any technical work).
> ⭐ This is the lab work methodology meant to be handed down.
> **Opening hook** (picking up Lesson 2's session pain): "Remember having to re-explain your research to it every time? Today you learn to fix that once and for all."
> **Core message**: **Claude forgets, but files don't. Write the memory into files and Claude reads it automatically every time.**
>
> **Main line vs. by-product (teaching design principle)**:
> - **Main line = solving "Claude forgets"** (a real need, easy to grasp, picks up the pain they felt firsthand in Lesson 2 → strongest motivation). The lesson openly teaches this.
> - **By-product = organizing your own knowledge assets** (writing CLAUDE.md so Claude remembers is, in fact, organizing the knowledge scattered in your head). Don't carry this as a banner or open with the abstract value — let it **emerge naturally** as learners write, and reveal it at the close.

---

## Three Files = Three Kinds of Memory (the teaching spine)

> Framing it as "Claude's three kinds of memory" is easier to grasp than "three files."

| File | Which memory | Answers | Analogy |
|------|--------------|---------|---------|
| **CLAUDE.md** | Long-term background memory | "What is this project?" | A **project briefing** for a new colleague (kept on the desk, read daily) |
| **PROGRESS.md** | Historical memory | "What have I done?" | A **lab notebook / clinical course record** |
| **TODO.md** | To-do memory | "What's left to do?" | A **to-do whiteboard** |

---

## 3-1 Why You Need It

- Re-enact "close it and it forgets" → make the pain concrete → solution: externalize memory into files.

## 3-2 CLAUDE.md (the Project Briefing)

- Put it in the project root; Claude reads it automatically when entering the folder.
- What goes in: research topic / where the data is / which tools / special rules (e.g., your cohort definition, a special grouped-modeling logic).
- **Key demo = ask the same question with vs. without a CLAUDE.md and watch the quality gap** (more convincing than ten sentences of explanation).
- → Each person fills in a CLAUDE.md for their own project on the spot.

**Starter template** (copy into `CLAUDE.md` in the project root; replace the brackets with your own):

```markdown
# [Project name, e.g. Burn Infection Outcome Analysis]

## What this is
[One or two sentences: research question + design, e.g. retrospective cohort predicting infection risk factors in hospitalized burn patients]

## Where the data is
- Main data: `./data/[cohort].csv` (de-identified, keyed by ID code)
- Data dictionary: `./data/codebook.md`

## Cohort definition
- Inclusion: [e.g. 2015–2024 acute burn admissions, TBSA ≥ 10%]
- Exclusion: [e.g. death within 24h of admission, missing key fields]

## Tools / conventions
- Python (pandas / scikit-learn / statsmodels)
- For imbalanced outcomes, report AUROC / AUPRC, not just accuracy
- Patient-level splits to avoid leakage

## Special rules / pitfalls hit
- [e.g. model L/R sides separately, never pooled]
- [e.g. infection defined per [some standard]]
```

> Rule: **only stable facts and rules go here**; to-dos go in TODO, history goes in PROGRESS (below).

## 3-3 PROGRESS.md (the Notebook)

- After finishing a chunk, tell Claude "log what I did today into PROGRESS."
- Use = cross-session memory + recalling "how I handled this back then" when writing the paper.
- For researchers: your annual report / paper progress rides on this.

**Template** (reverse order, newest on top):

```markdown
# PROGRESS — [Project name]

## 2026-06-21
- Finished cohort cleaning: 1,799 raw → 1,778 after exclusions (reasons below)
- Ran missingness analysis: `tbsa` 3.2% missing, `infection_flag` none
- Decision: impute age with the median (right-skewed, not the mean)
- Next steps in TODO

## 2026-06-18
- Received de-identified cohort, confirmed columns match the codebook
```

- Closing ritual: tell Claude "**log today's work into PROGRESS.md**" and it appends automatically.

## 3-4 TODO.md (the To-do Whiteboard)

- P0 (must-do) / P1 (secondary) prioritization.
- Collaborating with your supervisor: they read your TODO and immediately see where you're stuck (mirrors the lab's periodic progress report).
- **Only to-dos go here**: move done items to PROGRESS, delete dropped ones — don't let it pile up.

**Template**:

```markdown
# TODO — [Project name]

## P0 (this week)
- [ ] Complete Table 1 (baseline characteristics)
- [ ] Confirm the time window for the infection outcome (ask supervisor)

## P1 (later)
- [ ] Run logistic regression + compute OR / 95% CI
- [ ] Draw a forest plot
```

## 3-5 Tying the Habits Together

- A full project rhythm = set up CLAUDE.md → do the work → at the close, have it update PROGRESS / TODO → pick up seamlessly next time.

## 3-6 The Close — a Benefit You'll Gradually Discover (the by-product)

> The main line is done (solving "Claude forgets"). In the last minute, reveal the deeper value so it lands as a bonus, not a burden.

- The files you wrote so Claude would remember are, in fact, **you organizing your own knowledge**:
  - The scattered things in your head (how the cohort is defined, why these exclusions, what pitfalls you've hit, which papers you've read) → become a knowledge asset that is **written down, traceable, and handoff-ready**.
- Each file's second identity:
  - **CLAUDE.md** = your project's "knowledge master" (definitions / decisions / rules)
  - **PROGRESS.md** = your "research-journey sediment" (what you did and why → a goldmine when writing the paper)
  - **TODO.md** = your "next-step thinking"
- In one line: **writing it is organizing yourself now; once written, Claude happens to be able to use it — two birds, one stone.** The AI being able to read it is just a bonus; the real beneficiary is your future self.

---

## End of Lesson 3 — What the Learner Takes Away

- Each project **has a CLAUDE.md filled in on the spot** (immediately usable — ten times more useful than just grasping the concept).
- Can ask Claude to maintain PROGRESS / TODO.
- From "re-explaining every time" → "Claude remembers my project."

---

## To Produce / To Decide

- [x] ✅ Three templates (CLAUDE.md / PROGRESS.md / TODO.md) are embedded in sections 3-2/3-3/3-4 — a simplified three-file version; the full SSOT routing rules can wait until they're comfortable.
- [ ] Decide whether to spend class time "filling in a real CLAUDE.md on the spot" (strongly recommended yes).

---

*Status: draft outline. Content to be expanded chapter by chapter.*
