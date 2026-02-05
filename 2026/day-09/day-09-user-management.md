# Day 09 – Linux User & Group Management Challenge

## Task 1: Create Users `useradd`, `passwd`, `usermod`
### Create three users with home directories and passwords:
- Users: tokyo, berlin, professor
- Commands:
  - Create user with directory `sudo useradd -m tokyo`
  - Create or modify password `sudo passwd tokyo`
#### User created ✅
#### Verify: Check `/etc/passwd` and `/home/` directory

---

## Task 2: Create Groups `groupadd`, `groups`
### Create two groups:
- Groups: developers, admins
- Commands:
  - Create group `sudo groupadd developers`
#### Group created ✅
#### Verify: Check /etc/group

---

## Task 3: Assign to Groups `usermod`
### Assign users:
- tokyo → developers
  - Command: `sudo usermod -aG developers tokyo`
- berlin → developers + admins
  - Commands: `sudo usermod -aG developers berlin`, `sudo usermod -aG admins berlin`
- professor → admins
  - Command: `sudo usermod -aG admins professor`
#### Users assigned ✅
#### Verify: Use appropriate command to check group membership `cat /etc/group`

---

## Task 4: Shared Directory `chgrp`, `chmod`
#### 1. Create directory: /opt/dev-project
- Command: `sudo mkdir /opt/dev-project`
#### 2. Set group owner to developers
- Command: `sudo chgrp developers dev-project`
#### 3. Set permissions to 775 (rwxrwxr-x)
- Command: `sudo chmod 775 dev-project`
#### 4. Test by creating files as tokyo and berlin
- Commands:
  - tokyo: `su tokyo` → `cd /opt/dev-project` → `touch tokyo.md`
  - berlin: `su berlin` → `cd /opt/dev-project` → `touch berlin.md`

#### Verify: Check permissions and test file creation ✅

---

## Task 5: Team Workspace 
#### 1. Create user nairobi with home directory
- Command: `sudo useradd -m nairobi`
#### 2. Create group project-team
- Command: `sudo groupadd project-team`
#### 3. Add nairobi and tokyo to project-team
- Commands:
  - nairobi: `sudo usermod -aG project-team nairobi`
  - tokyo: `sudo usermod -aG project-team tokyo`
#### 4. Create /opt/team-workspace directory
- Command: `sudo mkdir /opt/team-workspace`
#### 5. Set group to project-team, permissions to 775
- Command: `sudo chgrp project-team team-workspace && sudo chmod 775 team-workspace`
#### 6. Test by creating file as nairobi
- Commands: `su nairobi` → `cd /opt/team-workspace` → `touch nairobi.md`




