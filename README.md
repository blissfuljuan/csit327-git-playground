# Git Playground (Fork Workflow) — AY 2025

A hands-on lab to practice **basic Git** with a real **GitHub PR workflow**.  
You will **fork** this repo, work on a **feature branch**, and open a **Pull Request** (PR) back to this class repo’s `main`.

> ✅ This repo has automated checks (GitHub Actions). Your PR will **fail** if:
> - Your **branch** does not start with **your GitHub username** (e.g., `ericrev/feature-readme`)
> - **README** does not list your **name + @username** under **Contributors**
> - Your **bio** file is missing or does not include **@username**
> - No **conventional commit** message or **issue number** in commits

---

## Objectives
- Practice **fork → branch → commit → push → pull request**
- Use **conventional commit messages** and reference issues
- Resolve a simple **merge conflict**
- Identify yourself clearly using your **GitHub username**

## Rules
- **Branch naming (required):** `your-github-username/feature-…`
- **Commit style:** Conventional Commits (e.g., `feat: …`, `docs: …`) and reference an issue `(#1)` or `(#2)`
- **Do not** push directly to `main`. Use a PR and request review.
- **Files to modify/add:** `README.md` (Contributors) and `students/<lastname>-<firstname>-bio.md`

## Prerequisites
- Git installed; GitHub account
- Perform Task A
- Configure your identity (once):
  ```bash
  git config --local user.name  "Your Name"
  git config --local user.email "your_email@example.com"
  ```

---

## Tasks (follow in order)

### A) Fork & clone
1. Click **Fork** (top-right) to create a copy under your GitHub account.
2. Clone **your fork** and inspect remotes:
   ```bash
   git clone <URL-of-your-fork>
   cd <your-fork-name>
   git remote -v
   ```
   *(Optional but useful):*
   ```bash
   git remote add upstream <URL-of-class-repo>
   ```

### B) Create a branch (must start with your GitHub username)
```bash
git switch -c <your-username>/documents-readme
```
Example: `blissfuljuan/documents-readme`

### C) Improve README (Issue #1)
Add **your real name + @username** under **Contributors** (see section at the bottom):
```
- Lastname, Firstname (**@your-github-username**)
```
Example:
```
- Doe, John (**@johndoe123**)
```
Commit:
```bash
git add README.md
git commit -m "docs(readme): add <lastnameL>, <firstname> to contributors (#1)"
```

### D) Add your bio (Issue #2)
Create `students/<lastname>-<firstname>-bio.md` with the following bullets (include your **@username**):
```markdown
- Year/Section: e.g., 3rd Year / G02
- Favorite Language: e.g., Java
- One Git Tip Learned: e.g., Use `git status` often
- GitHub: @your-github-username
```
Commit and push:
```bash
git add students/<lastname>-<firstname>-bio.md
git commit -m "docs(bio): add <lastname>, <firstname> student bio (#2)"
git push
```

### E) Push & open a Pull Request
```bash
git push -u origin <your-username>/documents-readme
```
Then open a **Pull Request** to **this class repo**’s `main`:
- **Title:** `docs: update README – Lastname, Firstname`
- **Body:** Mention **Issue #1** and describe your changes
- **Reviewer:** Request your instructor

### F) Sync and resolve conflicts (if any)
If your PR shows conflicts:
```bash
git fetch origin
git merge origin/main
# (Or if you set upstream earlier)
# git fetch upstream
# git merge upstream/main
# Resolve conflict markers in README.md, keep both your contributor line and class updates
git add README.md
git commit -m "fix: resolve README merge conflict"
git push
```

### G) Finalize
- Address any review comments
- When approved, **Squash merge** your PR

*(Optional bonus)*
```bash
git tag v0.1.<your-initials>
git push --tags
git restore README.md   # demo undo
```

---

## Commit Message Guide (Conventional Commits)
- **feat:** new feature — `feat(bio): add Doe student bio (#2)`
- **fix:** bug fix — `fix: resolve README merge conflict`
- **docs:** docs only — `docs(readme): add Doe to contributors (#1)`
- Others: `chore`, `refactor`, `test`, `style`, `perf`

Include an **issue number** in at least one commit: `(#1)` or `(#2)`.

---

## Cheatsheet
```bash
git status
git log --oneline --graph --decorate
git switch -c <branch>        # create/switch branch
git add <file>
git commit -m "type(scope): message (#issue)"
git push -u origin <branch>
git fetch origin && git merge origin/main
```

---

## Troubleshooting
- **Permission denied on push:** You’re pushing to the class repo. Ensure `origin` points to **your fork**.
- **Checks failing (branch name):** Rename branch to start with your **GitHub username**.
- **Checks failing (username missing):** Ensure `@your-username` appears in both **README (Contributors)** and your **bio** file.
- **No issue reference:** Amend/add a new commit including `(#1)` or `(#2)`.

---

## Contributors
- Macansantos, Axcel (**@AksilDev**)
