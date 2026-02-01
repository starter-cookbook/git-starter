---
title: Multi-Branch Flow
nav_order: 5
---

# Multi-Branch Flow

This workflow works well with 2-5 people when you want to maintain different environments.

With this workflow we will be dealing with two permanent branches: `main` and `develop` along with feature branches.

## Start your day

* Start on the `develop` branch

```bash
git checkout develop
git pull origin develop
```

## Create a feature branch

Branch off `develop`

```bash
git checkout develop
git checkout -b feature/my-branch
```

`feature/my-branch` is the name of your feature branch.  It can be named anything, but here are common naming examples:

* feature/add-homepage
* bugfix/fix-login-error
* chore/organize-files
* docs/document-setup

## Work on your feature

* Make changes locally
* Stage and commit

```bash
git add .
git commit -m "add a commmit message here"
```

## Keep your feature branch up-to-date (optional)

If you are working with others it is a good idea to merge `develop` back into your feature branch to keep your feature branch up to date with changes others have made.

```bash
git checkout develop
git pull origin develop
git checkout feature/my-branch
git merge develop
```

If merge conflicts appear you will need to resolve them.

## Push your feature branch

When you are ready to bring your feature branch into `develop` push your feature branch to your git host.

```bash
git push origin feature/my-branch
```

## Open a pull request (PR) into `develop`

1. Log into your git host
2. Opean a PR to merge your feature branch into `develop`
3. Request review from teammates if needed
4. After approval, merge into `develop`
5. After merge is complete you can delete your feature branch from your git host

`develop` can be used as an integration branch to test everyone's changes together.  You can also use it to deploy to a "dev" or "staging" environment where you can test changes before merging to `main` and going to production.

## Merge `develop` into `main` for production

Once `develop` is stable and tested, merge into `main`

1. Log into your git host
2. Create a PR from `develop` into `main`
3. Request review and approval if needed
4. When approved merge the PR
5. Do not delete `develop` after the merge.  `develop` should remain as your integration branch.

## Clean up

After your feature branch is merged into `develop` you can delete it.

```bash
git checkout develop
git pull origin develop
git branch -d feature/my-branch
```

If you did not delete your branch after you merged the PR on your git host you can delete it with:

```bash
git push origin --delete feature/my-branch
```

## Hotfixes

Sometimes you need to fix something in production immediately.  For these cases you can branch off `main`, creating a feature branch (i.e. `hotfix/fix-typo`) and then create PRs to merge the hotfix branch back into `main` and `develop`.

