# Git

## 3-States

- Working directory: what you're currently working on
- Staging: a 'drafting' area
- Repository: the permanent history

## Commands

```bash
# add them to a box befp
git add <file-selector>
git add .

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
```
