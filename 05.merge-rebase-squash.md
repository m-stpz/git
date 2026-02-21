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

| Goal                     | Where you should be (checkout) | Command                    |
| ------------------------ | ------------------------------ | -------------------------- |
| Merge feature into main  | `main`                         | `git merge feature-branch` |
| Rebase feature onto main | `feature-branch`               | `git rebase main`          |

- **Do not use Rebase on commits that've already pushed/shared on a remote repo!**
- Instead, use it for cleaning up your local commit history before merging it into a shared team branch

### Git Squash: The editor

- Allows us to take a long string of small, messy commits and condense them into a single, clean, meaningful commit
- Never squash commits that have already been pushed!
  - It's only for local development, to clean up the house

#### How to squash

Two ways:

1. Interactive rebase: see interactive-rebase.md
2. Lazy/Efficient: Squash merge

- Done when we want to bring our feature into main
- Instead of a regular merge, you tell git to "melt" all your feature branch commits into one single block

```bash
git checkout main
git merge --squash feature-branch
# puts all the changes in your "staging area", without commiting them
git commit -m "message for the commit"
```

- This way, `feature-branch` keeps its messy history, but the `main` branch only sees one clean commit
  - What about PRs, when we want to merge it our feature-branch into main?
