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

## The perfect commit

### 1. Add the right changes

- Selectively decide what should go into that commit
- Keep the commits and files selective
- Golden rule: **only combine changes from the same topic in a single commit**
- Create a very granular commit

#### Selecting a specific portion

- We can take a specific "chunk" of our changes and commit that, instead of the whole file
- We can either do it:

1.  through cli

```bash
git add -p <file> # then git will ask us what we want to include
```

2. through vscode's gui

2.1 open the working tree of the changes through vscode source control
2.2 select the portion you want to add
2.3 right click + "Stage selected ranges" (shortcut: cmd + k | cmd + option + s)

### 2. The message

1. Subject: concise summary of what happened
   - If you have difficulty explaining what happened, maybe there were too many things on that commit
2. Body: more detailed explanation
   - What's different?
   - Why did it change?
   - Anything worth mentioning?

## Branching strategies

- Consult/create a written best practice of how to structure it with your team

### Integrating changes & Structuring releases

1. Mainline development ("always be integrating")
   - few branches
   - relatively small commits
2. State, release, and feature branches
   - branches enhance structures & workflows
   - different types of branchs to fulfill different types of jobs

### Long-running & short-lived branches

#### Long-running

- Exists through the complete lifetime of the project
  - A longer "feature" / "fix" branch
  - Often, they mirro "stages" in your dev life cycle
- Integration branches

#### Short-lived

- Fow new features, bug fixes, refactoring, experiements
- Will be deleted after integration

## Merge conflicts

- They happend when integrating commits from different sources
- The same line of code was changed in two commits in two different branches

### Avoiding conflict hell

- We can't avoid them forever, but we can make them rarer and smaller

1. Pull often
2. Small commits
3. Communication
   - Going to refactor a major file? Tell your team!

### Reading a conflict

```js
<<<<<< HEAD // start of your local changes
const color = "red" // this is WHERE YOU'RE NOW
====== // the fence separating the 2 versions
const color = "blue" // this is WHAT YOU'RE PULLING IN
>>>>> main // >>>> [branch-name]: the end of the incoming changes
```

### How to solve it?

1. Decide what you want to do and delete the markers
2. Through VSCode, we can:
   - Accept current changes
   - Accept incoming changes
   - Accept both changes
   - Compare changes

## Merge vs. Rebase vs. Squash

- Merge: tells the story of how the work happened (including the messy parts)
- Rebase: tells the store of what the final project looks like

### Git merge: The preserver

- Merge commit: automatically created by git
  - When merged, git created a new "Merge commit".
  - Acts as a bridge, tying the 2 branches
  - It creates a diamond shape in your history
  - It's like a knot

```
             merge commit
c1 ------ c3 ----- c5 --- [branch-a] ---
    \ c2 --- c4 -- / ---- [branch-b] ---
```

Pros

- Non-destructive
- We can see when/where a branch was joined

Cons

- With many devs, the history can become a "spaghetti" of criss-crossing lines and "merge branch..." commits

```bash
# merge is done from "destination"
git checkout main # go to main
git merge feature-branch  # merge the feature-branch to <current-branch>
```

- I go to the destination [main] and I move into it the feature-branch

```bash
# I'm at main
git merge feature-branch  # feature-branch [changes] --- merged to ---> main [destination]
```

### Git rebase: The perfectionist

- Rebase takes the commits and moves them to the tip of the target branch
  - A perfeclty straight line
  - Looks like you developed the feature on the very latest version of the code

Pros

- Clean history
- Easy to follow

Cons

- Technically "faking" history
- If you rebase code that others have already downloaded, you'll cause massive sync errors for them

```bash
git checkout feature-branch
git rebase main
```

- It's done from the feature-branch

```bash
git checkout feature-branch # I go to the branch with the changes
git rebase main # I "lift" my work and put on top of the latest main
```

### Git Squash:

## To learn

- [] rebase | what are other options?
- [] stash
- [] cherry pick
- [] git lens
