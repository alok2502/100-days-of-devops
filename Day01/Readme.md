# Day 01 – Version Control System & Git Basics

## What I Learned

Today I revised the fundamentals of **Version Control Systems (VCS)** and understood why they are **absolutely essential in DevOps**.

In DevOps, we work with text all day — code, configuration files, YAMLs, scripts, manifests. These files are constantly **created, modified, and deleted**.  
A version control system helps track these changes, collaborate with teams, and safely roll back when something breaks.

---

## Why Version Control Is Necessary in DevOps

- Tracks changes to files over time
- Allows rollback to previous working versions
- Enables team collaboration
- Maintains history and accountability
- Prevents accidental data loss
- Forms the backbone of CI/CD pipelines

Without VCS, managing infrastructure and application code at scale is impossible.

---

## Types of Version Control Systems

### 1️⃣ Local Version Control System
- Backup copies are stored locally before making changes
- Rollback is possible only on the same machine

**Drawback:**
- No collaboration
- Risk of data loss
- Manual and error-prone

---

### 2️⃣ Centralized Version Control System (CVCS)
- A central server holds the main codebase
- Developers pull a working copy from the central server

**Drawbacks:**
- Single point of failure
- If the server is down, no one can work
- Limited offline capability

---

### 3️⃣ Distributed Version Control System (DVCS)
- Every developer has a full copy of the repository
- Work can continue even if the central server is down
- Changes are synced later

**This model solves the major drawbacks of CVCS.**

---

## Git & GitHub

- **Git** is a **Distributed Version Control System**
- **GitHub** is a **cloud-based platform** to host and collaborate using Git repositories

Git handles versioning locally, while GitHub provides remote storage, collaboration, and integration with CI/CD tools.

---

## Git Commands Practiced

### Repository Initialization
```bash
git init
```
### Staging & Committing
```bash
git add .
git commit -m "commit message"
```

### Pushing & Pulling
```bash
git push origin main
git pull
```

### Branch Management
```bash
git branch -m main          # Rename branch to main
git checkout -b branch1    # Create and switch to new branch
git branch                 # List branches
```

### Merging Branches
```bash
git checkout main
git merge branch1
```

### Viewing History & Changes
```bash
git log                    # View commit history
git show <commit-id>       # View changes in a commit
git diff                   # View uncommitted changes
```

### File Operations in Git
```bash
git rm <filename>          # Delete file and remove from index
git mv <old> <new>         # Move or rename files
```
---

## Rollback & Undo Strategies

### Undo Uncommitted Changes
```bash
git checkout -- <filename>
```

### Undo Staged Changes
```bash
git restore --staged <filename>
```

### Revert a Commit (Safe Rollback)
```bash
git revert HEAD
```
- Creates a new commit
- Preserves history (recommended for shared repos)

### Reset a Commit (History Rewrite)
```bash
git reset --hard <commit-id>
```
- Moves HEAD back
- Deletes commit history
- Should be used carefully

---

## Hands-on Practice Performed
- Created a Git repository
- Worked with branches
- Added content in a feature branch
- Merged changes into the main branch
- Pushed changes to a remote repository
- Deleted local repository
- Cloned the same repository again using git clone
- Practiced rollback using checkout, restore, revert, and reset

---

## Key Takeaways
- Version control is non-negotiable in DevOps
- Distributed VCS eliminates single points of failure
- Git enables safe experimentation using branches
- Understanding rollback commands is critical in real-world scenarios
- Git + GitHub forms the foundation of modern DevOps workflows

---