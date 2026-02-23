# Day 26 Assignment – GitHub CLI: Manage GitHub from Your Terminal
## Answer in your notes:
1. What authentication methods does `gh` support?
- `ssh` and `https`

2. How could you use `gh issue` in a script or automation?
- `gh issue` commands use in scripts and automation to create, list, edit, and close issues programmatically.

3. What merge methods does `gh pr merge` support?
- `merge commit`, `squash and merge`, and `rebase and merge`

4. How would you review someone else's PR using gh?
- Step 1: Check out the PR locally
  - `gh pr checkout <PR_number>`  This command fetches the associated branch and switches your local environment to it.
- Step 2: Review and test the code
- Step 3: Provide feedback and submit the review
  1. Comment: To leave general feedback without an explicit approval or request for changes.
    - `gh pr review <PR_number> --body "Great improvements overall."`
  2. Approve: To approve the changes for merging.
    - `gh pr review <PR_number> --approve --body "Looks good, merging when checks pass."`
  3. Request changes: To request modifications before the PR can be merged.
    - `gh pr review <PR_number> --request-changes --body "Please address the following issues..."`
- Step 4: Merge the PR
  - `gh pr merge <PR_number> --squash --delete-branch`

5. How could `gh run` and `gh workflow` be useful in a CI/CD pipeline? (Preview)
- The gh run and gh workflow commands in the GitHub CLI (Command Line Interface) are useful in a CI/CD pipeline for manual triggering, monitoring, and debugging workflows directly from the terminal, and for scripting automation within workflows themselves.
