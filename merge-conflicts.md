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
