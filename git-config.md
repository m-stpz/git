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

# no branch on remote? create it and link it to local
git config --global push.autoSetupRemote true # fixes the 'no upstream' error

git config --global fetch.prune true # automatically delete remote tracking branches that have been deleted
git config --global diff.algorithm histogram
git config --global merge.conflictstyle zdiff3

# make the diff tool vscode
git config --global diff.tool vscode # then, you'd type 'git difftool'
git config --global difftool.prompt false # now, it will be automatic
git config --global alias.dt difftool # create an alias for it

# merge tool
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait --merge $REMOTE $LOCAL $BASE $MERGED'
git config --global mergetool.prompt false
git config --global mergetool.keepBackup false
```

## Removing a property

```bash
git config --global --unset NAME VALUE
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
| `aa`  | `add .`      |
