# Day 38 Assignment – YAML Basics
## Task 1: Key-Value Pairs
Create `person.yaml` that describes yourself with:
- `name`
- `role`
- `experience_years`
- `learning` (a boolean)

**Verify:** Run `cat person.yaml` — does it look clean? No tabs?

- Output:
  ```
  aayushkumar@aayushs-MacBook-Air yaml % cat person.yml
  name: dhannu
  role: devops learner
  experience_years: 1
  learning: true%
  ```     
---
## Task 2: Lists
Add to `person.yaml`:

- `tools` — a list of 5 DevOps tools you know or are learning
- `hobbies` — a list using the inline format `[item1, item2]`

Write in your notes: What are the two ways to write a list in YAML?
- block style and flow style
  ```
  # Example of block style
  tools:
    - docker
    - kubernetes
    - git
    - ansible
    - terraform

  # Example of flow style
  hobbies: [traveling, listening to song]
  ```
---
## Task 3: Nested Objects
Create `server.yaml` that describes a server:

- `server` with nested keys: `name`, `ip`, `port`
- `database` with nested keys: `host`, `name`, `credentials` (nested further: `user`, `password`)

**Verify:** Try adding a tab instead of spaces — what happens when you validate it?
- No error is coming in my case.

---
## Task 4: Multi-line Strings
In `server.yaml`, add a `startup_script` field using:

The `|` block style (preserves newlines)
The `>` fold style (folds into one line)

Write in your notes: When would you use `|` vs `>`?
- pipe character `|`, is used when line breaks and trailing newlines are significant.
- greater-than character `>`, is used for long strings of text where line breaks in the YAML file are only for readability and should be treated as spaces in the final string.
---
## Task 5: Validate Your YAML
1. Install `yamllint` or use an online validator ✅
2. Validate both your YAML files ✅
3. Intentionally break the indentation — what error do you get?
- Output:
  ```
  All mapping items must start at the same column at line 8, column 1
  Nested mappings are not allowed in compact mappings at line 8, column 8
  Implicit keys need to be on a single line at line 8, column 8
  ```
4. Fix it and validate again ✅
- Output:
  ```
  Valid YAML!
  ```
---
## Task 6: Spot the Difference
Read both blocks and write what's wrong with the second one:
```
# Block 1 - correct
name: devops
tools:
  - docker
  - kubernetes
```
```
# Block 2 - broken
name: devops
tools:
- docker
  - kubernetes
```
- Indentation is not given in front of `- docker`.
