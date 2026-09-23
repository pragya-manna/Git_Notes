# Chapter 3: Branching & Merging

**Branch** — An independent line of development; lets you build a feature or fix a bug without affecting the stable `main` code until it's ready.

```bash
git branch                # list all local branches
git branch <name>          # create a new branch
git checkout <name>        # switch to an existing branch
git checkout -b <name>     # create a branch and switch to it in one step
git switch -c <name>       # modern equivalent of checkout -b
git branch -d <name>       # delete a branch (only if already merged, safe)
git branch -m old new      # rename a branch
```

**Merge** — Combines the changes from one branch into another, keeping full history and creating a special "merge commit" that has two parents.
```bash
git merge <branch>
```
- Safe to use on shared/public branches since it doesn't rewrite history.

**Rebase** — Takes the commits from your current branch and replays them on top of another branch, producing a clean, straight-line history (rewrites commit IDs).
```bash
git rebase <branch>       # move current branch's commits on top of another branch
git rebase -i HEAD~3      # interactively edit/squash/reorder the last 3 commits
```
- ⚠️ Never rebase a branch that others have already pulled/pushed — it rewrites history and breaks their copies.

**Merge vs Rebase (important for interviews)**
| Aspect | Merge | Rebase |
|---|---|---|
| History shape | Non-linear, but original history preserved | Linear, but commit hashes change |
| Safe on shared branch? | Yes | No |
| Typical use | Bringing a finished feature into main | Cleaning up your own local commits before opening a PR |

**Merge Conflict** — Occurs when Git cannot automatically combine two changes because the same lines were edited differently in both branches.
- Git marks the conflicting section in the file like this:
```
<<<<<<< HEAD
your current branch's version
=======
incoming branch's version
>>>>>>> branch-name
```
- **Resolution steps:** manually edit the file to keep the correct content → remove the markers → `git add <file>` → `git commit` (or `git rebase --continue` if mid-rebase).

**Common Branching Strategies**
- **Git Flow** — separate `main`, `develop`, `feature/*`, `release/*`, `hotfix/*` branches; good for scheduled/versioned releases.
- **GitHub Flow** — just `main` + short-lived feature branches merged via Pull Request; simple, good for continuous deployment.
- **Trunk-Based Development** — everyone commits directly to `main` frequently, using feature flags to hide unfinished work.