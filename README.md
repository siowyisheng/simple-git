# The Simple Guide to Git

_Git explained simply._

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/siowyisheng/simple-git/blob/master/LICENSE) ![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)

## Table of Contents <!-- omit in toc -->

- [What is Git?](#what-is-git)

## What is Git?

### How do remotes repositories work?

A remote repository first exists at a remote location; often, a github repo. When you `git clone` the repo, you create a **local copy** of the repo and the branches which **track** the remote repo's branches. You also create a **reference** to the remote repo and its branches.

### What is the difference between `git fetch` and `git pull`?

`git fetch` accesses the remote repo and updates your **reference** to the remote repo. `git pull` does a `git fetch` and also does a `git merge` to merge your reference to the remote branch with your local copy of the remote branch.

See [above](#how-do-remotes-repositories-work) to understand how remote repositories work.

### What are some common commands?

`git diff HEAD~1 HEAD` - View differences between this commit and the previous.

### How do I track the history of a file?

`gitk (filename)` or `git log -p (filename)`.

### How do I overwrite the remote after making a mistake?

`git push --force`

### How do I reset my local branch to copy the remote?

`git reset --hard origin/(your_branch_name)`

### How do I find a commit by the message?

`git log --all --grep='your search string'`

### How do I delete a local branch?

`git branch -D branch_name`

### How do I remove references to branches on the remote?

`git fetch --prune`

### How do I move recent commits to a new branch?

Scenario: You made 5 commits to `master` although you were supposed to work on a new branch.

```bash
git branch newbranch
git reset --hard HEAD~5
git checkout newbranch
```
