# Day 05 – Git Fundamentals & Branching Strategy

## Topics Covered
- What problem Version Control System solves
- Why Git is popular
- Centralized vs Distributed VCS
- Difference between Git and GitHub
- Git internal components
- Git lifecycle and core commands
- Branching concept and real-world example
- Branching strategy
- Commonly used Git commands

---

## What Problem Does Version Control System Solve?

Version Control System (VCS) mainly solves two problems:

1. Code sharing
2. Versioning of code

It allows multiple people to work on the same codebase while keeping track of changes and history.

---

## Why Git Is So Popular?

Git is popular because:
- It is a Distributed Version Control System (DVCS)
- Older systems like SVN and CVS are centralized
- Git removes single point of failure
- Faster, reliable, and scalable

---

## Centralized vs Distributed Version Control System

### Centralized VCS
- One central server holds the original copy
- Developers push changes to the central server
- Others can access code only after pushing
- If the central server is down, collaboration stops

### Distributed VCS (Git)
- Every developer has a full copy of the repository
- Developers can work independently
- Even if the central server is down, work continues
- This concept is often referred to as forking

Git solves the biggest limitation of centralized systems.

---

## Difference Between Git and GitHub

- Git is an open-source Distributed Version Control System
- GitHub is a cloud-based platform built on top of Git

GitHub provides additional features like:
- Code hosting
- Issues tracking
- Pull requests
- Project management
- Collaboration tools

We can say GitHub is a wrapper on top of Git that makes collaboration easy.

---

## Git Lifecycle (Core Workflow)

The basic Git lifecycle includes:
- git add
- git commit
- git push

### Repository Initialization
- git init is used to initialize an empty Git repository

---

## What Is Inside the .git Folder?

The .git directory contains important internal components:

### Objects
- Every file and change is stored as an object

### Refs
- References to branches and commits

### Hooks
- Used to enforce rules
- Example: Prevent pushing credentials or secrets

### Config
- Stores repository-level configurations
- Used for managing private credentials and settings

### HEAD
- Points to the current branch or commit

---

## Checking Repository Status

- git status shows tracked and untracked files
- git add is used to start tracking files
- git diff shows exact changes made to a file
- git commit saves a specific version
- git log shows commit history

---

## Rolling Back Changes

To move back to a previous version:
- git reset --hard commit-id

This resets the repository to a specific commit.

---

## Making Git Distributed Using GitHub

Everything discussed so far happens locally.

To make Git distributed and share code with others:
- Use GitHub as a remote repository
- Push local changes using git push
- Other developers can pull or clone the repository

---

## What Is a Branch?

A branch is a separate line of development.

Why branches are needed:
- To develop new features safely
- To avoid breaking the main code

---

## Real-World Example (Uber)

Uber has an existing cab feature.

If Uber wants to introduce a new bike feature:
- Developers create a feature_bike branch
- All changes are done in that branch
- If the feature is stable, it is merged into main
- If something breaks, the main branch remains safe

---

## Branching Strategy

A good branching strategy includes the following branches:

### Main / Master Branch
- Always stable
- Used for active development

### Feature Branch
- Created from main
- Used to develop new features
- Merged back to main after testing

### Release Branch
- Created when multiple features are ready
- Used for final testing and production release

### Hotfix Branch
- Created to fix production bugs
- Merged into both main and release branches

---

## Why Release Branch Is Needed?

- Main branch is always under active development
- Releasing directly from main is risky
- Release branch provides stability for production
- Allows bug fixes without blocking new development

---

## Common Git Commands Used Daily

- git init
- git status
- git add
- git commit
- git diff
- git log
- git push
- git pull
- git branch
- git checkout
- git merge
- git reset
- git clone

---

## Key Takeaways

- Git is a Distributed Version Control System
- It removes single point of failure
- GitHub enables collaboration and sharing
- Branching protects the main codebase
- A good branching strategy improves release quality

---

✅ Day 05 Completed – Git Fundamentals & Branching Strategy
