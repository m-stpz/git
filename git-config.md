# Git config

## Checking global config

```bash
git config --global --list # view all
git config --global user.name # view specific key
git config --global --edit # edit it
```

## Setting up new property

```bash
# git config --global NAME VALUE
git config --global init.defaultBranch main # sets the default init branch as main

# makes git stop complaining about 'the current branch has no upstream branch'
# if the branch doesn't exist on remote, create it and link them automatically
git config --global push.autoRemoteSetup true

git config --global fetch.prune true # automatically delete remote tracking branches that have been deleted
git config --global diff.algorithm histogram
git config --global merge.conflictstyle zdiff3
```

## Global aliases

### Creating aliases

Instead of typing long commands, you can create shorter versions

- They are stored in `.gitconfig`
- If you find yourself typing long commands like `git log --oneline --graph --all` often, create a shortcut:

```bash
git config --global alias.<alias-name> "log --all --decorate --oneline --graph"
```

| alias | full command |
| ----- | ------------ |
| `st`  | `status`     |
| `co`  | `checkout`   |
| `br`  | `branch`     |
| `cm`  | `commit -m`  |
| `ps`  | `push`       |
