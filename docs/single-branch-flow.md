---
title: Single Branch Flow
nav_order: 3
---

# Single Branch Flow - for solo work

This is a basic workflow if you are working on a repository all by yourself.

The workflow has one branch and commits directly to that branch.

No branches other than `main`.  This is one of the simplest workflows for git.

{: .warning }
This workflow is not recommended if you work with others. If not used carefully it can lead to more merge conflicts and overwritten changes.

## Start your day

Update your local copy of the `main` branch with what is on your remote branch.

If you are working alone this may be needed if you work on your repository from different computers or if you commit directly to your repo on your remote host.

```bash
git checkout main
git pull origin main
```

## Work on your code

* Make changes directly on `main`
* Commit frequently with commit messages

```bash
git add .
git commit -m "put your commit message here"
```

## Push your changes to your remote

```bash
git push origin main
```
