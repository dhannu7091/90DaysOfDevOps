# Day 40 Assignment – Your First GitHub Actions Workflow

## 📁 Hands-on repository
- [github-actions-zero-to-hero](https://github.com/dhannu7091/github-actions-zero-to-hero)

- [github-actions-practice](https://github.com/dhannu7091/github-actions-practice)

---
### Task 1: Set Up ✅
1. Create a new **public** GitHub repository called `github-actions-practice`
2. Clone it locally
3. Create the folder structure: `.github/workflows/`

---

### Task 2: Hello Workflow ✅
Create `.github/workflows/hello.yml` with a workflow that:
1. Triggers on every `push`
2. Has one job called `greet`
3. Runs on `ubuntu-latest`
4. Has two steps:
   - Step 1: Check out the code using `actions/checkout`
   - Step 2: Print `Hello from GitHub Actions!`

Push it. Go to the **Actions** tab on GitHub and watch it run.

**Verify:** Is it green? Click into the job and read every step.

---

### Task 3: Understand the Anatomy ✅
Look at your workflow file and write in your notes what each key does:
- `on:` Defines the events that trigger the workflow, such as push, pull_request, or schedule.
- `jobs:` A collection of steps that run together on the same runner. Jobs can run in parallel by default.
- `runs-on:` Specifies the type of machine or environment (runner) to use for the job (e.g., ubuntu-latest, windows-latest).
- `steps:` An ordered sequence of tasks executed within a job.
- `uses:` References an external action to be executed in a step, such as actions/checkout@v4.
- `run:` used to execute command-line shell scripts or commands on the runner machine
- `name:` (on a step) Provides a descriptive label for a specific step in the logs

---

### Task 4: Add More Steps ✅
Update `hello.yml` to also:
1. Print the current date and time
2. Print the name of the branch that triggered the run (hint: GitHub provides this as a variable)
3. List the files in the repo
4. Print the runner's operating system

Push again — watch the new run.

---

### Task 5: Break It On Purpose ✅
1. Add a step that runs a command that will **fail** (e.g., `exit 1` or a misspelled command)
2. Push and observe what happens in the Actions tab
3. Fix it and push again

Write in your notes: What does a failed pipeline look like? How do you read the error?
- Showing red status
- To understand why a pipeline failed, follow these steps:
1. Go to the repository Actions tab
2. Click on the failed workflow run
3. Select the failed job
4. Open the failed step
5. Read the logs displayed in the step output
- Output:
  ```
    Run exit 1
  Error: Process completed with exit code 1.
  ```
