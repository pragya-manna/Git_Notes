# Chapter 5: Undoing Changes, Advanced Tools & Interview Prep

**git restore** — Discards changes in the working directory or unstages files, without touching commit history.
```bash
git restore <file>              # discard unstaged changes in a file
git restore --staged <file>     # unstage a file (keep its changes in working dir)
```

**git reset** — Moves the current branch pointer to a different (usually earlier) commit; can optionally also change staged/working files.
```bash
git reset --soft HEAD~1     # undo last commit, but keep its changes staged
git reset --mixed HEAD~1    # undo last commit, changes go back to unstaged (default mode)
git reset --hard HEAD~1     # undo last commit AND permanently delete its changes ⚠️
```

**git revert** — Creates a brand-new commit that undoes the effect of an earlier commit, without deleting or rewriting any history.
```bash
git revert <hash>
```

**Reset vs Revert (important for interviews)**
| Aspect | Reset | Revert |
|---|---|---|
| Effect on history | Rewrites/removes commits | Preserves history, adds a new "undo" commit |
| Safe on shared/pushed branches? | No | Yes |
| Typical use | Undoing local mistakes not yet pushed | Undoing a commit that's already public/shared |

**Advanced Tools**
- **git cherry-pick** — Applies one specific commit from another branch onto your current branch, without merging the whole branch.
```bash
git cherry-pick <hash>
```
- **git bisect** — Automatically performs a binary search through commit history to find exactly which commit introduced a bug.
```bash
git bisect start
git bisect bad              # mark current commit as broken
git bisect good <commit>    # mark a known working commit
```
- **git reflog** — Shows a log of every place HEAD has pointed to, even after resets or deletions; the main way to recover "lost" commits.
```bash
git reflog
```
- **git submodule** — Lets you include another Git repository as a subfolder inside your project, tracked at a specific commit.
```bash
git submodule add <url> <path>
```
