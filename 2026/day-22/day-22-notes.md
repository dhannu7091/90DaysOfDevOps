# Day 22 – Introduction to Git: Your First Repository

## Task 1 to 5 Completed ✅

## Task 6: Understand the Git Workflow
Answer these questions in your own words (add them to a day-22-notes.md file):

1. What is the difference between git add and git commit?
- `git add` used for untracked to stage a file and `git commit` used for staged to tracked
2. What does the staging area do? Why doesn't Git just commit directly?
- In the staging area, you can decide which changes go into commits. If everything were committed directly, every small change would result in a separate commit. Staging gives you control, allowing you to make clean, sensible commits.
3. What information does git log show you?
- git log` shows who made the commit and when
4. What is the .git/ folder and what happens if you delete it?
- .git/ folder conains commit history, branches, staging area everything in there. once you delete it, the directory become a normal folder with your files, but all virsion control history and tracking are lost
5. What is the difference between a working directory, staging area, and repository?
- We work in the working directory and in the staging area we decide which changes to commit and the repository holds all the Git data.
