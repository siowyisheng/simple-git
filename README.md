# The Simple Guide to Git

_Git explained simply._

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/siowyisheng/simple-git/blob/master/LICENSE) ![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)

## Table of Contents <!-- omit in toc --- [What is Git?](#what-is-git)

- [How do remotes repositories work?](#how-do-remotes-repositories-work)

  - [What is the difference between `git fetch` and `git pull`?](#what-is-the-difference-between-git-fetch-and-git-pull)
  - [What are some common commands?](#what-are-some-common-commands)
  - [How do I track the history of a file?](#how-do-i-track-the-history-of-a-file)
  - [How do I overwrite the remote after making a mistake?](#how-do-i-overwrite-the-remote-after-making-a-mistake)
  - [How do I reset my local branch to copy the remote?](#how-do-i-reset-my-local-branch-to-copy-the-remote)
  - [How do I find a commit by the message?](#how-do-i-find-a-commit-by-the-message)
  - [How do I delete a local branch?](#how-do-i-delete-a-local-branch)
  - [How do I remove references to branches on the remote?](#how-do-i-remove-references-to-branches-on-the-remote)
  - [How do I move recent commits to a new branch?](#how-do-i-move-recent-commits-to-a-new-branch)
  - [How do i](#how-do-i)>

- [What is Git?](#what-is-git)

## What is Git?

## What are semantic commits?

Prepending each commit with a type, for easier organization of commits. It is often referenced from the [Karma runner conventions](http://karma-runner.github.io/0.10/dev/git-commit-msg.html).

feat: adds some new feature
fix: fixes some bug
content: changes some values/strings/content only (no actual code change)
test: adds tests
refactor: refactors some section
docs: changes some documentation
chore: updates build (no code change)
perf: improves performance of some section (by refactoring)
style: formats some section

## How do remotes repositories work?

A remote repository first exists at a remote location; often, a github repo. When you `git clone` the repo, you create a **local copy** of the repo and the branches which **track** the remote repo's branches. You also create a **reference** to the remote repo and its branches.

## What is the difference between `git fetch` and `git pull`?

`git fetch` accesses the remote repo and updates your **reference** to the remote repo. `git pull` does a `git fetch` and also does a `git merge` to merge your reference to the remote branch with your local copy of the remote branch.

See [above](#how-do-remotes-repositories-work) to understand how remote repositories work.

## What are some common commands?

`git diff HEAD~1 HEAD` - View differences between this commit and the previous.

## How do I track the history of a file?

`gitk (filename)` or `git log -p (filename)`.

## How do I overwrite the remote after making a mistake?

`git push --force`

## How do I reset my local branch to copy the remote?

`git reset --hard origin/(your_branch_name)`

## How do I find a commit by the message?

`git log --all --grep='your search string'`

## How do I delete a local branch?

`git branch -D branch_name`

## How do I remove references to branches on the remote?

`git fetch --prune`

## How do I move recent commits to a new branch?

Scenario: You made 5 commits to `master` although you were supposed to work on a new branch.

```bash
git branch newbranch
git reset --hard HEAD~5
git checkout newbranch
```

## How do I check which files were edited between two commits?

`git diff --name-only HEAD~1 HEAD`

## How do I stash just one or a few files?

```bash
git stash save -p
```

From there, use:

- `a` to add the file to the stash
- `d` to ignore the file
- `q` to ignore the rest of the files

## How do I see changes of all recent commits?

```bash
git log -p
```

## How do I see an overview of what recent commits touched?

```bash
git log --stat
```

## How do I amend my last commit message?

```bash
git commit --amend
```

## How do I add a file to a commit?

```bash
git commit -m 'initial commit'
git add forgotten_file
git commit --amend
```

## How do find all commits that added or removed a certain string?

```bash
git log -S "dude, where's my car?" --source --all
git log -G "^(\s)*function foo[(][)](\s)*{$" --source --all
```