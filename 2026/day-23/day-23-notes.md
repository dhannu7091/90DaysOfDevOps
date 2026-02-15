# Day 23 – Git Branching & Working with GitHub

## Task 1: Understanding Branches
Answer these in your day-23-notes.md:

1. What is a branch in Git?
- A branch in Git is a place where we can separate our work from the main history. Each branch has its own commit, so we can work on individual files without changing the main branch.
2. Why do we use branches instead of committing everything to `main`?
- Branches are used to keep the `main` code stable. New features or changes are made on a separate branch, keeping the main branch clean and production-ready. Only when everything is finalized are they merged into the `main` branch, so that bugs or incomplete changes don't go directly to the `main` branch.
3. What is `HEAD` in Git?
- `HEAD` tells us which branch we are currently in and where the latest commit is.
4. What happens to your files when you switch branches?
- When we change branches, Git changes the files in our working directory to reflect the new branch. Only the files that are in that branch will be visible.

### Answer in your notes: 
5. What is the difference between `origin` and `upstream`?
- `origin` is a self-created repository and `upstream` forked someone else's repository
6. What is the difference between `git fetch` and `git pull`?
- `git fetch` updates the local repository but does not merge or add any changes; it simply downloads new branches and updates from the remote. `git pull` directly fetches and merges changes.

7. What is the difference between `clone` and `fork`?
- `git clone` is used to create a copy of a repository. `git fork` is used to create a copy of a repository so that both the changes in the original repository and your own changes can be synced.
8. When would you `clone` vs `fork`?
- We use `git clone` when we only need a single copy of the repository. We use `git fork` to create a copy where we make our commits and also sync the commits from the original repository.
9. After forking, how do you keep your fork in sync with the original repo?
- using `sync fork`
