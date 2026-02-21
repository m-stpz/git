# Git

## 3-States

- Working directory: what you're currently working on
- Staging: a 'drafting' area
- Repository: the permanent history

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

## Understanding `HEAD` and `~` (Navigation)

- `HEAD` is a pointer to where you're right now. Current "Current chapter" indicator in a book

### Tilde: `~` (backwards in time)

- `~` is used to look back at previous commits **relative** to your current position
  - `HEAD`: last commit you made
  - `HEAD~1`: the commit before the last
  - `HEAD~3`: 3 commits ago

If you want to undo the last 2 commits, but keep the code changes in folder:

```bash
git reset --soft HEAD~2
```

## Pulling a colleague's branch

It's not necessary to

- This was the old way

```bash
git fetch origin <remote-branch-name>
git checkout -b <local-branch-name> origin/<remote-branch-name>
```

Simply

```bash
git fetch origin # update remote list
git checkout <branch-name> # switch to their branch
# it will grab the remote branch
# branch 'b-1' set up to track 'origin/b-1'.
# Switched to a new branch 'b-1'

# other options
git switch <branch-name> # modern "switch"
git checkout -b <local-name> origin/<branch-name> # if you want to change the name | old way
```

### `git fetch` vs. `git fetch origin`

- `git fetch origin`: tell git exactly which remote to talk to
  - use it if you have multiple remotes

```bash
git remote # checks all remotes you're connected to
git remove -v # verbose
```

- `git fetch`: git decides which remote to fetch from
  - if your current branch tracks a specific rremove, git automatically fetches from that remote

- Both commands are "safe" commands. Meaning, it downloads the data, but doesn't change your local
  - you can also run `git fetch --all`: your local machine is now in sync with every single remote server

- How to check if remote has changed?

```bash
git fetch
git status # this will show you

# your branch is up to date with origin/main
# your branch is behind 'origin/main' by <n> commits and can be fast-forwarded
```
