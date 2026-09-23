# Chapter 2: Basic Workflow (Saving & Tracking Changes)

**git status** — Shows which files are modified, staged, or untracked right now.
```bash
git status
```

**git diff** — Shows the exact line-by-line changes.
```bash
git diff             # changes not yet staged
git diff --staged    # changes staged but not yet committed
```

**git add** — Moves changes from the working directory into the staging area (marks them "ready to commit").
```bash
git add <file>     # stage one specific file
git add .          # stage all changed files
git add -p         # stage changes in small chunks (useful to split unrelated edits)
```

**git commit** — Saves the staged changes permanently as a new snapshot in history.
```bash
git commit -m "message"     # commit with a message
git commit -am "message"    # stage all tracked file changes + commit together
git commit --amend          # edit the most recent commit (message or add missed files)
```

**Commit message convention** — Write a short summary of *what* changed, and if needed, *why* (the diff already shows the "what" in detail).
```
feat: add login form validation
fix: correct total price calculation in cart
```

**git log** — Shows commit history.
```bash
git log --oneline          # compact, one line per commit
git log --graph --all      # visual branch/merge structure
git show <hash>             # full details of one specific commit
git blame <file>             # shows who last edited each line of a file
```

**.gitignore** — A file listing patterns of files/folders Git should never track (e.g., passwords, build output, dependencies).
```
node_modules/
.env
*.log
```
**Why:** Keeps the repo clean and prevents accidentally leaking secrets or bloating history with generated files.