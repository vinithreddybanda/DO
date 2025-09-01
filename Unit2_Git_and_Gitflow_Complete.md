# Unit 2: Git and Gitflow – Complete Guide (Beginner to Advanced)

---

## Table of Contents
1. [What is Git? (Theory & Overview)](#1-what-is-git-theory--overview)
2. [Git Installation](#2-git-installation)
3. [Initial Setup & Configuration](#3-initial-setup--configuration)
4. [Git Vocabulary (Key Terms)](#4-git-vocabulary-key-terms)
5. [Understanding the Git Process (Theory)](#5-understanding-the-git-process-theory)
6. [Essential Git Command Lines (Beginner to Advanced)](#6-essential-git-command-lines-beginner-to-advanced)
7. [Branching, Merging, and Conflict Resolution](#7-branching-merging-and-conflict-resolution)
8. [Advanced Git Concepts & Workflows](#8-advanced-git-concepts--workflows)
9. [Gitflow Pattern & Branching Strategy (Theory & Practice)](#9-gitflow-pattern--branching-strategy-theory--practice)
10. [Gitflow Commands (Practical)](#10-gitflow-commands-practical)
11. [Advanced GitHub & Team Workflows](#11-advanced-github--team-workflows)
12. [Best Practices & Tips](#12-best-practices--tips)
13. [Summary](#13-summary)

---

## 1. What is Git? (Theory & Overview)

Git is a Distributed Version Control System (VCS) created by Linus Torvalds in 2005. It is the backbone of modern collaborative software development (used by GitHub, GitLab, Bitbucket, etc.).

**Key Features:**
- Distributed: Every developer has a full copy of the repository history.
- Tracks changes in code, text, and other files.
- Enables collaboration without overwriting others’ work.
- Allows reverting to earlier versions and working offline.
- Supports branching, merging, and advanced workflows.

**Why use Git?**
- Reliable, fast, and secure.
- Enables open-source and enterprise collaboration.
- Supports complex workflows (feature branches, code reviews, CI/CD).

**How Git Works:**
- Git stores data as snapshots (not differences) of your project over time.
- Each commit is a snapshot with a unique hash.
- Branches are lightweight pointers to commits.
- Merging combines changes from different branches.

---

## 2. Git Installation

### Windows
- Download from [git-scm.com](https://git-scm.com/)
- Run the installer and follow the prompts

### macOS
- Use Homebrew: `brew install git`
- Or download from [git-scm.com](https://git-scm.com/)

### Linux
- Debian/Ubuntu: `sudo apt-get install git`
- Fedora: `sudo dnf install git`

---

## 3. Initial Setup & Configuration

Set your identity (required for commits):
```sh
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```
Set default editor (optional):
```sh
git config --global core.editor "code --wait"  # VS Code
```
View all config:
```sh
git config --global --list
```
Other useful config:
```sh
git config --global color.ui auto
git config --global init.defaultBranch main
```

---

## 4. Git Vocabulary (Key Terms)

- **Repository (repo):** Project folder tracked by Git
- **Commit:** A snapshot of changes
- **Branch:** A parallel version of the repository
- **Merge:** Combine changes from different branches
- **Clone:** Copy a remote repository locally
- **Remote:** A version of the repository hosted elsewhere (e.g., GitHub)
- **Staging Area (Index):** Where changes are prepared before commit
- **HEAD:** Current branch reference
- **Tag:** A named pointer to a specific commit (often for releases)
- **Fork:** A personal copy of someone else’s repository (GitHub)
- **Pull Request (PR):** A request to merge changes from one branch/repo to another

---

## 5. Understanding the Git Process (Theory)

Git works in three main areas:
- **Working Directory:** Where you edit files.
- **Staging Area (Index):** Where you prepare files for commit (`git add`).
- **Repository:** Where commits are stored (`git commit`).

**Typical workflow:**
1. Edit files
2. `git add` (stage changes)
3. `git commit` (save snapshot)
4. `git push` (share with remote)

---

## 6. Essential Git Command Lines (Beginner to Advanced)

### 6.1. Repository Setup
```sh
git init                # Initialize a new repository
git clone <url>         # Clone a remote repository
```

### 6.2. Workflow Basics
```sh
git status              # Show changed files
git add <file>          # Stage file(s) for commit
git add .               # Stage all changes
git commit -m "message" # Commit staged changes
git log                 # View commit history
```

### 6.3. Branching
```sh
git branch              # List branches
git branch <name>       # Create new branch
git checkout <name>     # Switch to branch
git checkout -b <name>  # Create and switch to new branch
git merge <name>        # Merge branch into current branch
git branch -d <name>    # Delete branch
```

### 6.4. Remote Repositories
```sh
git remote -v           # List remotes
git remote add origin <url> # Add remote

git push origin <branch>    # Push branch to remote
git pull origin <branch>    # Pull changes from remote
git fetch                 # Fetch changes (no merge)
```

### 6.5. Undo & Reset
```sh
git reset <file>        # Unstage file
git checkout -- <file>  # Discard changes in file
git revert <commit>     # Create a new commit that undoes a commit
git reset --hard <commit> # Reset to a specific commit (dangerous)
```

---

## 7. Branching, Merging, and Conflict Resolution

### 7.1. Branch Management
```sh
git branch                # List branches
git branch <name>         # Create branch
git checkout <name>       # Switch branch
git switch <name>         # (newer syntax)
git branch -m old new     # Rename branch
git branch -d <name>      # Delete branch (safe)
git branch -D <name>      # Force delete
```

### 7.2. Merging & Conflict Handling
```sh
git merge <branch>        # Merge into current branch
git merge --abort         # Cancel a merge
# Conflict resolution:
# Edit file → git add <file> → git commit
```

### 7.3. Comparing & Visualizing
```sh
git log --graph --oneline --decorate --all
git diff branch1 branch2
git diff --name-only
```

---

## 8. Advanced Git Concepts & Workflows

### 8.1. Stash (Save Work Temporarily)
```sh
git stash                # Save changes
git stash list           # List stashes
git stash pop            # Restore last stash & remove it
git stash apply          # Restore last stash (keep it)
git stash drop           # Delete last stash
git stash clear          # Delete all stashes
```

### 8.2. Rebase (Linear History)
```sh
git rebase branchname            # Reapply commits onto another branch
git pull --rebase                # Update without merge commits
git rebase -i HEAD~N             # Interactive rebase (edit/squash/reorder)
```

### 8.3. Cherry-Pick (Selective Commit Transfer)
```sh
git cherry-pick <commit-id>      # Apply specific commit to current branch
```

### 8.4. Bisect (Find Bug-Introducing Commit)
```sh
git bisect start
git bisect bad
git bisect good <commit-id>
# Mark each test as good/bad until found
git bisect reset
```

### 8.5. Archive (Export Snapshot)
```sh
git archive --format=zip --output=project.zip HEAD
```

### 8.6. Cleaning Workspace
```sh
git clean -n    # Preview untracked files to delete
git clean -f    # Delete untracked files
```

### 8.7. Tags (Releases)
```sh
git tag v1.0.0
git tag -a v1.0.0 -m "First release"
git push origin v1.0.0
git tag
git show <tag>
git push origin --tags
git tag -d v1.0.0
git push origin --delete v1.0.0
```

### 8.8. Comparing
```sh
git diff branch1 branch2
git diff commit1 commit2
git diff --name-only
git diff --stat
```

### 8.9. Useful Shell Commands for Git Practice
```sh
echo "text" > file.txt
echo "text" >> file.txt
cat file.txt
touch file.txt
rm file.txt
ls
pwd
clear
```

---

## 9. Gitflow Pattern & Branching Strategy (Theory & Practice)

Gitflow is a branching model for managing features, releases, and hotfixes in a consistent way.

### 9.1. What is Gitflow?
Gitflow is a branching model that standardizes how features, releases, and hotfixes are managed. It helps teams work in parallel and keep code stable.

**Main Branches:**
- **main/master:** Production-ready code
- **develop:** Integration branch for features

**Supporting Branches:**
- **feature/**: New features (`feature/feature-name`)
- **release/**: Release preparation (`release/v1.0`)
- **hotfix/**: Quick fixes to production (`hotfix/urgent-fix`)

### 9.2. Gitflow Branching Example (Step-by-Step)
```sh
git checkout develop
git checkout -b feature/my-feature   # Start a feature branch
# ... work, commit ...
git checkout develop
git merge feature/my-feature         # Merge feature back to develop
git checkout -b release/v1.0         # Start a release branch
# ... test, fix ...
git checkout main
git merge release/v1.0               # Merge release to main
# Tag release
git tag v1.0
git checkout develop
git merge release/v1.0               # Merge release back to develop
```

---

## 10. Gitflow Commands (Practical)

Install git-flow extension (if not included):
```sh
# macOS/Linux
brew install git-flow
# Windows (Git Bash)
git flow init
```

### Initialize Gitflow in a Repo
```sh
git flow init
```

### Start a Feature
```sh
git flow feature start my-feature
# ... work, commit ...
git flow feature finish my-feature
```

### Start a Release
```sh
git flow release start v1.0
# ... test, fix ...
git flow release finish v1.0
```

### Start a Hotfix
```sh
git flow hotfix start urgent-fix
# ... fix ...
git flow hotfix finish urgent-fix
```

---

## 11. Advanced GitHub & Team Workflows

### 11.1. Pull Requests (PRs)
- Propose changes from a branch to be merged into another (main/master).
- Enables code review, discussion, and approval before merging.
- Merge options: merge commit, squash & merge, rebase & merge.

### 11.2. Fetch vs Pull vs Push
- `git fetch`: Download changes, don’t merge.
- `git pull`: Fetch + merge (or rebase).
- `git push`: Upload your commits to remote.

### 11.3. Team Workflow Example
```sh
git pull --rebase origin main
git checkout -b feature-x
# work, commit
git push -u origin feature-x
# Open PR, review, merge
git branch -d feature-x
git push origin --delete feature-x
```

### 11.4. Forks & Upstream
- Fork: Your own copy of a repo (no write access to original).
- Add upstream: `git remote add upstream <url>`
- Sync: `git fetch upstream && git merge upstream/main`

### 11.5. Tags & Releases on GitHub
- Create tag: `git tag v1.0.0`
- Push tag: `git push origin v1.0.0`
- Delete remote tag: `git push origin --delete v1.0.0`

### 11.6. Cherry-pick Workflow with PRs
- Cherry-pick commit, push branch, open PR, merge.

### 11.7. Collaborators & Permissions
- Add collaborators in GitHub repo settings.

### 11.8. Forks & Open Source Contribution
- Fork, clone, add upstream, sync, branch, PR.

### 11.9. Remote Info & Tracking
```sh
git remote -v
git remote show origin
git branch -vv
```

### 11.10. Check Out PR Locally
```sh
git fetch origin pull/123/head:pr-123
git checkout pr-123
```

### 11.11. Change Default Branch Name
```sh
git branch -m master main
git push -u origin main
git push origin --delete master
```

### 11.12. Authentication Tips
- HTTPS with PAT, SSH keys, credential managers.

### 11.13. GitHub Pages
- Publish static sites from main/docs or gh-pages branch.

### 11.14. Clean Up Remote Tags/Branches
```sh
git push origin --delete <branch>
git push origin --delete <tag>
```

### 11.15. PR Review Basics
- Review, comment, approve, merge, delete branch.

---

## 12. Best Practices & Tips
- Commit often with clear messages
- Use branches for features and fixes
- Pull before you push
- Review changes before merging
- Protect main/master branch
- Use `.gitignore` to avoid committing unwanted files
- Tag releases for easy reference
- Rebase for a clean history (but avoid rebasing shared branches)
- Use stashing to save work in progress
- Clean up merged branches
- Use annotated tags for releases
- Always check status and diff before committing

---

## 13. Summary

Git is a powerful, flexible, and essential tool for modern software development. Mastering its commands, workflows, and advanced concepts (like Gitflow, rebase, bisect, and PRs) will help you collaborate, manage code, and deliver high-quality software efficiently.

---

For more, see the [Pro Git Book](https://git-scm.com/book/en/v2), [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials), and the official [GitHub Docs](https://docs.github.com/).
