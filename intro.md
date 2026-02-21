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
