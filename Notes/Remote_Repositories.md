# Chapter 4: Remote Repositories & Collaboration

**Remote** — A version of your repository hosted elsewhere (e.g., on GitHub), used to share work with others.
```bash
git remote -v                     # list connected remotes and their URLs
git remote add origin <url>       # connect this local repo to a remote, naming it "origin"
```

**Fetch vs Pull vs Push**
- **git fetch** — Downloads new commits from the remote but does NOT merge them into your branch; lets you review changes before combining them.
```bash
git fetch
```
- **git pull** — Downloads new commits AND immediately merges them into your current branch (`fetch` + `merge` combined).
```bash
git pull
git pull --rebase     # same, but rebase instead of merge for a cleaner history
```
- **git push** — Uploads your local commits to the remote repository so others can see them.
```bash
git push
git push -u origin <branch>       # push and remember this branch's upstream (only needed once)
git push --force-with-lease       # safely overwrite remote history, but fails if someone else pushed first
```

**git stash** — Temporarily saves your uncommitted changes so you can switch tasks/branches with a clean working directory, then restore them later.
```bash
git stash          # save current changes and clean the working directory
git stash pop       # reapply the most recent stash and remove it from the stash list
git stash list       # see all saved stashes
git stash apply       # reapply a stash but keep it in the list too
```

**git tag** — Marks a specific commit with a permanent, meaningful label — typically used for release versions (unlike branches, tags don't move).
```bash
git tag v1.0.0                        # lightweight tag
git tag -a v1.0.0 -m "release note"    # annotated tag (stores author, date, message — preferred)
git push origin --tags                 # upload tags to the remote
```

**Open Source Contribution Workflow** — The standard step-by-step process used to contribute to a project you don't own:
1. **Fork** the repository on GitHub (creates your own copy under your account).
2. **Clone** your fork to your machine: `git clone <your-fork-url>`
3. **Link the original repo** as "upstream": `git remote add upstream <original-url>`
4. **Sync with upstream** before starting: `git fetch upstream` then `git merge upstream/main`
5. **Create a feature branch**: `git checkout -b fix/issue-123`
6. Make your changes and commit them.
7. **Push to your fork**: `git push -u origin fix/issue-123`
8. **Open a Pull Request (PR)** on GitHub, from your branch into the original repo's `main`.
9. Respond to reviewer comments, push more commits if needed.
10. Once approved, the maintainer merges it — you can delete your branch afterward.