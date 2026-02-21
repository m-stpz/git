# Interactive rebase

- Clean up your work before anyone sees it

```bash
git rebase -i HEAD~3 # Look at my last 3 commits
```

And editor will pop up - You can't squase "up", only "down", into the commit above it

- Chronological order (oldest at the top, newest at the bottom)

```txt
pick <commit-num-1> <commit-message> # this one must be at the "base", we can't put 's' here
pick <commit-num-2> <commit-message> # we can put s
pick <commit-num-3> <commit-message> # we can put s

# Rebase commands:
# p, pick: use commit
# s, squash: use commit, but melt into previous one => combines code + asks you to combine the messages
# f, fixup: combines code + discards the messages of the squashed commits
```

## Interactive rebase commands

```
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup [-C | -c] <commit> = like "squash" but keep only the previous
```

Once this is done (CTRL + X) and save, another editor will appear where you can select the message

- It'll open an editor
