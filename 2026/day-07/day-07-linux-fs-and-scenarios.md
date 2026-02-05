# Day 07 – Linux File System Hierarchy & Scenario-Based Practice
## Part 1: Linux File System Hierarchy (30 minutes)
### Core Directories
- `/` (root) - It holds critical system binaries, configuration files, libraries, and user data. It acts as the starting point for the entire file system tree. 
- `/home` - User home directories where personal files are stored.
- `/root` - The home directory for the root user (separate from /).
- `/etc` - System-wide configuration files and scripts.
- `/var/log` - `/var` Variable data files, including logs (`/var/log`) and databases.
- `/tmp` - Temporary files, often cleared on reboot.
### Additional Directories
- `/bin` - Essential command binaries needed for system operation.
- `/usr/bin` - Contains the primary executables for user commands that are not essential for system booting or basic maintenance (those are in `/bin` or `/sbin`).
- `/opt` - Stands for "optional." It is used for add-on or third-party software that keeps its files self-contained, usually in a subdirectory named after the application (e.g., `/opt/application/`).
### Hnads-on task:
```
# Find the largest log file in /var/log
du -sh /var/log/* 2>/dev/null | sort -h | tail -5

# Look at a config file in /etc
cat /etc/hostname

# Check your home directory
ls -la ~
```
## Part 2: Scenario-Based Practice (40 minutes)
### Scenario 1: Service Not Starting
```
A web application service called 'myapp' failed to start after a server reboot.
What commands would you run to diagnose the issue?
Write at least 4 commands in order.
```
Answer:
```
Step 1: `systemctl status nginx`
Why: To check service running or not

Step 2: `journalctl -u nginx -n 50`
Why: Checking logs to see any errors

Step 3: `systemctl is-enabled nginx`
Why: To check is it enabled to start on boot
```
### Scenario 2: High CPU Usage
```
Your manager reports that the application server is slow.
You SSH into the server. What commands would you run to identify
which process is using high CPU?
```
Answer:
```
Step 1: `htop`
Why: To check live cpu usage

Step 2: `ps aux --sort=-%cpu | head -10`
Why: Sort top 10 process who using high cpu

Step 3: Note the PID of the top process
```
### Scenario 3: Finding Service Logs
```
A developer asks: "Where are the logs for the 'docker' service?"
The service is managed by systemd.
What commands would you use?
```
Answer:
```
Step 1: `systemctl status docker`
Why: Check service status first

Step 2: `journalctl -u docker -n 50`
Why: View last 50 lines of logs

Step 3: `journalctl -u docker -f`
Why: Show live logs
```
### Scenario 4: File Permissions Issue
```
A script at /home/user/backup.sh is not executing.
When you run it: ./backup.sh
You get: "Permission denied"

What commands would you use to fix this?
```
Answer:
```
Step 1: check current file permission
Command: `ls -l /home/user/backup.sh`
Look for: -rw-rw-r-- (no 'x' = not executable)

Step 2: change file permission
Command: `chmod 764 /home/user/backup.sh`

Step 3: verify file permission
Command: `ls -l /home/user/backup.sh`
Look for: -rwxrw-r-- ('x' = executable)

Step 4: retry to run script
Command: `./backup.sh`
```

