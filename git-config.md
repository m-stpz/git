# Git config

## Checking global config

```bash
git config --global --list # view all
git config --global user.name # view specific key
git config --global --edit # edit it
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
