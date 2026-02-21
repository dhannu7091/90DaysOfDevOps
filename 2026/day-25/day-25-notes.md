# Day 25 – Git Reset vs Revert & Branching Strategies
## Task 1: Git Reset — Hands-On
Answer in your notes:
1. What is the difference between `--soft`, `--mixed`, and `--hard`?
- `--soft` reverts only the HEAD point, but the stage and working directory remain the same.
- `--mixed` reverts both the HEAD and stage, but the working directory remains the same.
- `--hard` resets the entire commit, stage, and working directory to the previous changes.

2. Which one is destructive and why?
- `--hard` is the most destructive, as it completely erases the working directory and any staged changes.

3. When would you use each one?
- `--soft` is used when you want to change the commits, but keep the staging and working directories the same.
- `--mixed` is used when you want to reset the staging area, but keep the changes in the working directory.
- `--hard` is used when you want to completely erase all previous changes; this resets both the history and the files.

4. Should you ever use `git reset` on commits that are already pushed?
- No, not at all. Resetting to previously pushed commits changes the history shared with others, which can lead to conflicts and confusion.

---
## Task 2: Git Revert — Hands-On
Answer in your notes:
1. How is `git revert` different from `git reset`?
- `git revert` creates a new commit that reverses the changes from the previous commit, thus preserving history and reflecting the reversed changes in the record.
- `git reset` simply pushes history back, erasing previous commits but replacing the previously created record.

2. Why is `revert` considered safer than `reset` for shared branches?
- `git revert` is considered more secure because it doesn't change history, but rather adds a new commit that reverses the old changes. This way, everyone has a consistent, shared history. In contrast, reset changes history, removing old commits, which can mess with other histories, cause conflicts, and cause problems for collaborators.

3. When would you use `revert` vs `reset`?
- `git revert` is used when you're working on a shared branch and need to safely reverse a change, leaving history unchanged and allowing everyone to see the changes clearly.
- `git reset` is used when you want to discard changes locally, especially when you need to completely reset to an earlier commit.
---
## ask 3: Reset vs Revert — Summary
Create a comparison in your notes:

| | `git reset` | `git revert` |
|---|---|---|
| What it does | push back the previous commit | reverse the previous commit with a new commit |
| Removes commit from history? | Yes | No |
| Safe for shared/pushed branches? | No | Yes |
| When to use | when you want to discard changes locally | when you're working on a shared branch and need to safely reverse a change |

---
## Task 4: Branching Strategies
Answer:
1. Which strategy would you use for a startup shipping fast?
- GitHub flow or Trunk-Based Development (simple, fast, low process overhead)

2. Which strategy would you use for a large team with scheduled releases?
- GitFlow (structured, controlled, release-focused)

3. Which one does your favorite open-source project use? (check any repo on GitHub)
- Example:
  - Linux Kernel → merge-based workflow
  - Kubernetes → mostly PR-based + squash/merge strategy
