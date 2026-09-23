# Chapter 1: Fundamentals

**Git** — A Distributed Version Control System (DVCS) that tracks changes to files over time, so you can see history, collaborate, and revert if needed. Created by Linus Torvalds (2005).

**Version Control** — A system that records changes to files so you can recall specific versions later.

**Git vs GitHub**
- **Git** = the actual tool/software that runs on your machine and manages version history.
- **GitHub** = a website that hosts Git repositories online and adds collaboration features (Pull Requests, Issues, code review).

**Why Git is popular**
- Distributed → full project history is stored on your own laptop, so you can work offline.
- Fast → most commands run locally, not over network.
- Cheap branching → creating a branch takes a second, encourages experimentation.
- Data integrity → every change is hashed (SHA), so corruption/tampering is detectable.

**The Three Areas of Git**
| Area | Definition |
|---|---|
| Working Directory | The actual folder on your disk where you edit files. |
| Staging Area (Index) | A holding zone where you list exactly which changes will go into the next commit. |
| Repository (.git folder) | The database where all committed history is permanently stored. |

**Basic Flow:** Edit file → `git add` (stage it) → `git commit` (save snapshot) → `git push` (upload to remote server).

**Key Internal Concepts**
- **Blob** — the stored content of a file (not its name).
- **Tree** — represents a folder structure, links filenames to blobs.
- **Commit** — a saved snapshot of the project at a point in time; stores a message, author, timestamp, and a pointer to the previous commit.
- **HEAD** — a pointer that tells Git "which commit/branch you are currently on."
- **Branch** — a movable label pointing to a commit; used to work on features separately from the main code.

**Setup Commands**
```bash
git --version                          # check Git is installed and its version
git config --global user.name "Name"   # set the name attached to your commits
git config --global user.email "mail"  # set the email attached to your commits
git config --list                      # view all current config settings
git init                               # start tracking a new folder as a Git repo
git clone <url>                        # download a full copy of an existing remote repo
```

---
