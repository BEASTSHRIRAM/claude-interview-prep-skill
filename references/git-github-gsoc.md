# Git, GitHub and GSoC Reference

---

## Git Basics — Must Know Commands

### Setting Up

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### Starting a Repository

```bash
git init                      # initialize a new local repo
git clone <url>               # clone a remote repo to your machine
```

### The Daily Workflow

```bash
git status                    # see what has changed
git add filename.java         # stage a specific file
git add .                     # stage all changes
git commit -m "your message"  # save staged changes with a message
git push origin main          # push commits to remote
git pull origin main          # fetch and merge latest from remote
```

### Branching

```bash
git branch                    # list all branches
git branch feature-login      # create a new branch
git checkout feature-login    # switch to that branch
git checkout -b feature-login # create and switch in one step
git merge feature-login       # merge branch into current branch
git branch -d feature-login   # delete branch after merging
```

### Undoing Things

```bash
git restore filename.java     # discard unstaged changes in a file
git reset HEAD filename.java  # unstage a file
git revert <commit-hash>      # undo a commit by creating a new commit
git log --oneline             # see commit history in short form
```

---

## GitHub Workflow for Open Source

### Step 1 — Fork the Repository
Go to the project on GitHub and click Fork. This creates your own copy under your account.

### Step 2 — Clone Your Fork

```bash
git clone https://github.com/YOUR_USERNAME/project-name.git
cd project-name
```

### Step 3 — Add Upstream Remote
This lets you pull in changes from the original repo.

```bash
git remote add upstream https://github.com/ORIGINAL_OWNER/project-name.git
git remote -v    # verify both origin and upstream are set
```

### Step 4 — Create a Feature Branch
Never work directly on main. Always create a new branch per feature or fix.

```bash
git checkout -b fix/orange-rotting-bug
```

### Step 5 — Make Changes, Commit, Push

```bash
git add .
git commit -m "fix: handle edge case when no fresh oranges exist"
git push origin fix/orange-rotting-bug
```

### Step 6 — Open a Pull Request (PR)
Go to your forked repo on GitHub. You will see a "Compare and Pull Request" button. Click it.

**A good PR description includes:**
- What problem does this solve
- How did you solve it
- Screenshots or output if applicable
- Issue number it closes (example: Closes #42)

### Step 7 — Keep Your Fork Updated

```bash
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

---

## Writing Good Commit Messages

Follow this format:

```
type: short description in present tense

type can be:
  feat      — new feature
  fix       — bug fix
  docs      — documentation change
  style     — formatting, no logic change
  refactor  — code restructure, no behavior change
  test      — adding tests
  chore     — dependency updates, config changes
```

Examples:

```
feat: add multi-source BFS for rotten oranges
fix: handle empty matrix edge case in BFS
docs: update README with setup instructions
```

---

## Google Summer of Code (GSoC) — Complete Guide

### What is GSoC
GSoC is a global program where Google pays students to contribute to open source organizations over a summer. You get a stipend (roughly 1500 to 3300 USD depending on country), a mentor, and a real open source contribution on your resume.

### Timeline (Approximate, Check Official Site Each Year)
| Phase | When |
|---|---|
| Organizations announced | February / March |
| Student applications open | March |
| Application deadline | April |
| Accepted students announced | May |
| Coding period | May to August |
| Final evaluation | August / September |

### Step 1 — Choose an Organization

Go to summerofcode.withgoogle.com and browse accepted organizations.

Look for orgs that:
- Use a tech stack you know (Java, Python, JavaScript, C++)
- Have an active community on GitHub or mailing lists
- Have beginner friendly issues labeled `good first issue` or `help wanted`

Good orgs for beginners: GNOME, Wikimedia, OpenMRS, Sugar Labs, Joomla, Apache, Python Software Foundation

### Step 2 — Start Contributing Early (3 to 4 Months Before Deadline)

Do not wait until applications open. Orgs select students they already know.

```
1. Join their mailing list or Discord / Slack
2. Set up the project locally and get it running
3. Read the contributing guide (usually CONTRIBUTING.md)
4. Fix one small bug or improve documentation
5. Open a PR. Get it reviewed and merged.
6. Introduce yourself in the community
```

Even one merged PR before applying increases your chances significantly.

### Step 3 — Write a Winning Proposal

This is the most important part. A bad proposal with good contributions loses. A great proposal with one merged PR wins.

**Proposal Structure:**

```
1. About Me
   Name, college, year, tech stack, links to GitHub and LinkedIn

2. Project Summary
   What is the project, why does it matter, what will you deliver

3. Goals and Deliverables
   Week by week breakdown of what you will build
   Be specific. "Implement BFS based graph traversal module with unit tests by week 3"

4. Timeline
   Community bonding period (what you will learn and set up)
   Coding period week by week milestones
   Buffer week for review and polish

5. Why You
   Your relevant skills, past contributions to this org, related projects

6. Why This Project
   Show you understand the codebase. Reference specific files or issues.

7. Post GSoC Plans
   Show you will stay in the community after the program ends
```

**Tips for the proposal:**
- Keep it under 5 pages but information dense
- Reference your merged PRs and community interactions
- Get it reviewed by your mentor before submitting
- Submit at least 3 days before the deadline

### Step 4 — During GSoC

```
Weekly blog post or progress report
Daily or every 2 day sync with your mentor
Push code frequently, do not disappear for a week
Write tests for everything you build
Document your code as you go
```

### Step 5 — Common Mistakes That Get Applications Rejected

1. Submitting a generic proposal without reading the project idea page
2. Never contributing before applying
3. Copy pasting the project description as your deliverables
4. Vague timelines like "implement the module" with no detail
5. Ignoring the community and only DMing the mentor directly
6. Asking mentors for guidance without doing any research first. Always show your legwork before asking a question.
7. Applying to a project where 2 or more students are already actively contributing. Too much competition, find a less crowded project.
8. Submitting the proposal the day it is due. Submit early and ask for mentor feedback on your draft.

---

## Real GSoC Experiences (Anonymous)

### Student A — Java Based Project

Key lesson: "If you can not express your questions clearly, it is useless. Learn how to write an excellent bug report or question so that the mentor can help you faster."

Approach: Read the entire manual of the package they were working on, asked both how and why questions, and was patient during the one third of GSoC spent just understanding the codebase.

### Student B — Machine Learning Org

Key lesson: Check the mailing lists of organizations before applying. If no one has expressed interest in a project, that is your opening.

Approach: Learned a new language from scratch just for this project, built a working prototype before GSoC even started, and had half the project done before the first evaluation.

### Student C — Computational Geometry Org

Key lesson: Domain mismatch is not a blocker. Willingness to learn and early contact with the mentor is what gets you in.

### Student D — AI Algorithms Org

Key lesson: GSoC is not about knowing everything. It is about being comfortable learning fast under a real project deadline.

---

## The Unwritten Rules of Open Source

1. Never DM a mentor directly without introducing yourself on the public mailing list or chat first.
2. When you are stuck, state all the things you already tried before asking.
3. Read the CONTRIBUTING.md file before touching a single line of code.
4. Your first PR does not have to be a big feature. Fix a typo in the docs, improve a README, close a beginner issue.
5. The community bonding period is not a holiday.
6. Post weekly updates publicly even if your mentor does not ask for them.
7. GSoC is not an internship. Treat it as your biggest open source contribution, not as a job.

---

## GitHub Profile Tips for Interviews and GSoC

1. Pin your 4 to 6 best repositories on your profile
2. Write a README for every project you want to show
3. Use GitHub Actions for CI so interviewers see green checks
4. Contribute to at least one external open source project
5. Keep your contribution graph green consistently

### A Good Repository README Has:
```
- Project title and one line description
- Demo screenshot or GIF
- Tech stack badges
- How to run locally (step by step)
- Features list
- Contributing guide
- License
```

---

## Interview Questions on Git

1. What is the difference between git merge and git rebase?
2. What does git stash do and when do you use it?
3. How do you resolve a merge conflict?
4. What is the difference between git fetch and git pull?
5. What is a detached HEAD state?
6. How do you squash multiple commits into one?

### Key Answers

**git merge vs git rebase**
Merge creates a new merge commit preserving full history. Rebase rewrites commit history to appear linear. Use merge for shared branches, rebase for cleaning up local feature branches before merging.

**git fetch vs git pull**
Fetch downloads changes from remote but does not apply them. Pull does fetch plus merge in one command. Fetch is safer when you want to inspect changes first.

**Resolving a merge conflict**
Open the conflicting file, look for conflict markers, manually pick the correct code, remove the markers, then git add and git commit.

**git stash**
Temporarily shelves your uncommitted changes so you can switch branches without committing incomplete work. Use git stash pop to bring them back.
