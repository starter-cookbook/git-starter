---
title: Single Branch with Feature Branches
nav_order: 4
---

# Basic git workflow for a small team

This workflow is a basic git workflow for a small team of more than 1 member.

This workflow can also be used as a solo developer if you want an extra layer of protection before pushing to `main`

This workflow uses a single branch `main`, feature branches and pull requests.

## Start your day

* Start on `main`
* Update your local `main` with the latest changes

```bash
git checkout main
git pull origin main
```

## Create a feature branch

* Create a feature branch for your work

```bash
git checkout -b feature/my-branch
```

`feature/my-branch` is the name of your feature branch.  It can be any valid file-like naming.

Examples of feature branch names:

* feature/login-form
* bugfix/fix-nav
* docs/update-readme
* chore/organize-files

## Work on you code

* Make your changes locally

## Stage and commit your changes

Stage your changes

```bash
git add .
```

Commit your changes

```bash
git commit -m "a commimt message"
```

## Sync your branch with `main`

Optionally you can pull down changes made to main while you were working on your local branch.

This is useful if others have been updating `main` while you worked on your branch.

```bash
git checkout main
git pull origin main
git checkout feature/my-branch
git merge main
```

* `feature/my-branch` is your feature branch
* If there are merge conflicts you will need to resolve them

## Push your changes to your remote

```bash
git push origin feature/my-branch
```

This makes your feature branch visible to the team on your remote repo and ready for a pull request.

## Create a pull request (PR)

1. Log into your remote repo (github, gitlab, bitbucket)
2. Open a PR from your feature branch into `main`
3. Add a title and description for your PR
4. Tag a team member for review if needed
5. Create the pull request

## Code review and merge

1. Review the pull request and comment as needed
2. If changes are needed make them on the same branch

  ```bash
  git add .
  git commit -m "additional changes from code review"
  git push origin feature/my-branch
  ```

3. Once approved, merge the PR into `main` using your git host's web UI
4. After the merge is complete your git host should have the option to delete your feature branch.  This will delete your branch from the remote host.

## Local clean up

After your PR is merged you can delete you local branch

```bash
git checkout main
git pull origin main
git branch -d feature/my-branch
```

### Optional remote clean up

If you do not use your git host to delete the remote branch after the merge is complete you can also do it with the following command.

```bash
git push origin --delete feature/my-branch
```
