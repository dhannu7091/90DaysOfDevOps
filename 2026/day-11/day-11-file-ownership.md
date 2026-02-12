# Day 11 – File Ownership Challenge (chown & chgrp)

## Task 1: Understanding Ownership (10 minutes)
### 1. Run `ls -l` in your home directory
- Command: `ls -l`
### 2. Identify the owner and group columns
- First column is owner and second column is group
### 3. Check who owns your files
- My files owns ubuntu user and ubuntu group
#### Format: -rw-r--r-- 1 owner group size date filename ✅
### Document: What's the difference between owner and group?
- Answer:
  - Owner: Owner has primary control over the file and make changes in file (read, write, execute, delete). owner can modify its permissions and change its group ownership.
  - Group: group have access rights as defined by the group's permissions for a specific file. This simplifies permission management for multiple users working on shared projects.

---

## Task 2: Basic chown Operations (20 minutes)
### 1. Create file `devops-file.txt`
- Command: `touch devops-file.txt`
### 2. Check current owner: `ls -l devops-file.txt`
- Command: `ls -l devops-file.txt`
  - Output:
    ```
    -rw-rw-r-- 1 ubuntu ubuntu 0 Feb  7 11:35 devops-file.txt
    ```
### 3. Change owner to `tokyo` (create user if needed)
- Command: `sudo chown tokyo devops-file.txt`
  - Output:
    ```
    -rw-rw-r-- 1 tokyo ubuntu 0 Feb  7 11:35 devops-file.txt
    ```
### 4. Change owner to `berlin`
- Command: `sudo chown berlin devops-file.txt`
  - Output:
    ```
    -rw-rw-r-- 1 berlin ubuntu 0 Feb  7 11:35 devops-file.txt
    ```
### 5. Verify the changes ✅
### Try:
```
sudo chown tokyo devops-file.txt
```

---

## Task 3: Basic chgrp Operations (15 minutes)
### 1. Create file `team-notes.txt`
- Command: `touch team-notes.txt`
### 2. Check current group: `ls -l team-notes.txt`
- Command: `ls -l team-notes.txt`
  - Output:
    ```
    -rw-rw-r-- 1 ubuntu ubuntu 0 Feb 12 08:42 team-notes.txt
    ```
### 3. Create group: `sudo groupadd heist-team`
- Command: `sudo groupadd heist-team`
### 4. Change file group to `heist-team`
- Command: `sudo chgrp heist-team team-notes.txt`
### 5. Verify the change
- Command: `ls -l team-notes.txt`
  - Output:
    ```
     -rw-rw-r-- 1 ubuntu heist-team 0 Feb 12 08:42 team-notes.txt
    ```

---

## Task 4: Combined Owner & Group Change (15 minutes)
#### Using `chown` you can change both owner and group together:

### 1. Create file `project-config.yaml`
- Command: `touch project-config.yaml`
### 2. Change owner to `professor` AND group to `heist-team` (one command)
- Command: `sudo chown professor:heist-team project-config.yaml`
### 3. Create directory `app-logs/`
- Command: `mkdir app-logs`
### 4. Change its owner to `berlin` and group to `heist-team`
- Command: `sudo chown berlin:heist-team app-logs`
#### Syntax: `sudo chown owner:group filename`

---

## Task 5: Recursive Ownership (20 minutes)
### 1. Create directory structure:
```
mkdir -p heist-project/vault
mkdir -p heist-project/plans
touch heist-project/vault/gold.txt
touch heist-project/plans/strategy.conf
```
- Commands:
  - `mkdir -p heist-project/vault`
  - `mkdir -p heist-project/plans`
  - `touch heist-project/vault/gold.txt`
  - `touch heist-project/plans/strategy.conf`
### 2. Create group `planners`: `sudo groupadd planners`
- Command: `sudo groupadd planners`
### 3. Change ownership of entire `heist-project/` directory:
  - Owner: `professor`
  - Group: `planners`
  - Use recursive flag (`-R`)
    - Command: `sudo chown -R professor:planners heist-project/`
### 4. Verify all files and subdirectories changed: `ls -lR heist-project/`
- Command: `ls -lR heist-project/`
  - Output:
    ```
    heist-project/:
    total 8
    drwxrwxr-x 2 professor planners 4096 Feb 12 13:08 plans
    drwxrwxr-x 2 professor planners 4096 Feb 12 13:07 vault

    heist-project/plans:
    total 0
    -rw-rw-r-- 1 professor planners 0 Feb 12 13:08 strategy.conf
    
    heist-project/vault:
    total 0
    -rw-rw-r-- 1 professor planners 0 Feb 12 13:07 gold.txt
    ```

---

## Task 6: Practice Challenge (20 minutes)
### 1. Create users: `tokyo`, `berlin`, `nairobi` (if not already created)
- Already created ✅
### 2. Create groups: `vault-team`, `tech-team`
- Commands:
  - `sudo groupadd vault-team`
  - `sudo groupadd tech-team`
### 3. Create directory: `bank-heist/`
- Command: `mkdir bank-heist/`
### 4. Create 3 files inside:
  ```
  touch bank-heist/access-codes.txt
  touch bank-heist/blueprints.pdf
  touch bank-heist/escape-plan.txt
  ```
- Commands:
  - `touch bank-heist/access-codes.txt`
  - `touch bank-heist/blueprints.pdf`
  - `touch bank-heist/escape-plan.txt`
### 5. Set different ownership:
- `access-codes.txt` → owner: `tokyo`, group: `vault-team`
  - Command: `sudo chown tokyo:vault-team bank-heist/access-codes.txt`
- `blueprints.pdf` → owner: `berlin`, group: `tech-team`
  - Command: `sudo chown berlin:tech-team bank-heist/blueprints.pdf`
- `escape-plan.txt` → owner: `nairobi`, group: `vault-team`
  - Command: `sudo chown nairobi:vault-team bank-heist/escape-plan.txt`
### Verify: `ls -l bank-heist/`
- Command: `ls -l bank-heist/`
  - Output
    ```
    total 0
    -rw-rw-r-- 1 tokyo   vault-team 0 Feb 12 13:20 access-codes.txt
    -rw-rw-r-- 1 berlin  tech-team  0 Feb 12 13:20 blueprints.pdf
    -rw-rw-r-- 1 nairobi vault-team 0 Feb 12 13:20 escape-plan.txt
    ```
