# Commands

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
