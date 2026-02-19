# Day 24 – Advanced Git: Merge, Rebase, Stash & Cherry Pick
## Task 1: Git Merge — Hands-On
Answer in your notes:
1. What is a fast-forward merge?
- A fast-forward merge occurs when there are no new commits on the target branch, and Git simply pushes the branch forward without creating a new merge commit.

2. When does Git create a merge commit instead?
- Git creates a merge commit when two branches have different histories. That is, if both have new commits, Git creates a new "merge commit" to combine them, so that the two histories become one.

3. What is a merge conflict? (try creating one intentionally by editing the same line in both branches)
- A merge conflict occurs when the same line has been changed differently in both branches, and Git can't decide which one to keep.

---
## Task 2: Git Rebase — Hands-On
Answer in your notes:
1. What does rebase actually do to your commits?
- Rebase takes your commits and places them on a new base, changing their history.

2. How is the history different from a merge?
- A merge keeps the history of both branches together, while a rebase changes the history into a straight line.

3. Why should you never rebase commits that have been pushed and shared with others?
- Never rebase previously pushed and shared commits, as this changes history and causes confusion for others.

4. When would you use rebase vs merge?
- Rebase is used when you want to keep the history clean, and merge is used when you want to preserve the complete history of different branches.

---
## Task 3: Squash Commit vs Merge Commit
Answer in your notes:
1. What does squash merging do?
- Squash merges multiple smaller commits into a single commit, making the history clean and concise while recording all changes simultaneously.
2. When would you use squash merge vs regular merge?
- Squash merges are used when you want to clean up the commit history and combine small commits into a single commit, while regular merges are used when you want to keep the history complete and with different commits, so that the full path of changes is visible.
3. What is the trade-off of squashing?
- The trade-off with squashing is that you simplify and clean up the commit history, but you lose the detail and chronological record of individual changes. This means that the details are no longer visible, only the final result is clearly visible.
---
## Task 4: Git Stash — Hands-On
Answer in your notes:
1. What is the difference between git stash pop and git stash apply?
- git stash pop applies the changes and removes the stash from the list, while git stash apply only applies the changes but keeps the stash, allowing you to use it later.

2. When would you use stash in a real-world workflow?
- Stash is used when you're working on something but need to leave it to do something more important—it saves your changes, allowing you to resume work later.

---
## Task 5: Cherry Picking
Answer in your notes:
1. What does cherry-pick do?
- Cherry-pick pulls a specific commit into another branch without merging the entire branch, allowing you to move just the necessary changes to a separate branch.

2. When would you use cherry-pick in a real project?
- You use cherry-pick when you only need the changes from a specific commit, but not the entire branch history or merges, such as an important bug fix or a small feature that only needs to be in one place.

3. What can go wrong with cherry-picking?
- Conflicts can occur when cherry-picking, because Git places the commit in a new location, and if the old commits and the new changes don't match, the conflict will have to be resolved manually, and the history may look a bit messy.
