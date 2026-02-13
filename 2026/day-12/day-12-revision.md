# Day 12 – Breather & Revision (Days 01–11)

## Mini Self-Check (write short answers)

### 1. Which 3 commands save you the most time right now, and why?
1. `ls -l filename` Only the permissions and ownership of the required file will be visible, not for all files.
2. `grep` `awk` finding exact keyword/error in logs which you want.
3. `chown` change group and owner in one command.

### 2. How do you check if a service is healthy? List the exact 2–3 commands you’d run first.
1. `systemctl status <service>` to check service running or not
2. `htop` to check cpu and memory usage
3. `df -h` to check disk usage

### 3. How do you safely change ownership and permissions without breaking access? Give one example command.
- Command: `sudo chown berlin hello.txt && sudo chmod 660 hello.txt`

### 4. What will you focus on improving in the next 3 days?
- i'm improving shell scripting in next 3 days
