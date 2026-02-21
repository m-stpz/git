# Commands

## Questions

- How to check the global config?
- What does '~' mean in git?

## Project initialization

- Setting up environment

```bash
git init # create .git folder
git clone <url> # copes existing repo from server to machine
git config --global user.name "Your name"
```

## Checking global config

```bash
git config --global --list # view all
git config --global user.name # view specific key
git config --global --edit # edit it
```

## Staging & Commiting

```bash
git status # shows which files are modified

# Adding file(s)
git add <file>
git add .
git add -p # iterates through changes and allows you to select which one you want to use
git commit -m "msg"
git commit --amend -m # fixes last message
```

## Branching & context switching

```bash
git branch
git checkout <name>
git checkout -b <name>
git switch - # handy shortcut to jump back to previous branch you were on
git branch -d <name>
```

```bash
# add them to a box befp
git add <file-selector>
git add .
git add -p <file> # we can then select which portion we add to that commit

# taking a snapshot
git commit -m "<message>"

# upload changes
git push origin <branch>

# create a new branch
git checkout -b <new-branch>

# staying up to date
git fetch # downloads the latest info fomr server, but doesn't change your local file
git pull # fetch + merge

# undoing changes
git restore --staged <file-name> # unstage a file
git restore <file-name> # discard local changes
git commit --amend -m "Corrected message" fix last commit message

# check your branches
git branch

# checking changes
git diff

# checking history
git log

# stopping a merge
git merge --abort
git rebase --abort
```
