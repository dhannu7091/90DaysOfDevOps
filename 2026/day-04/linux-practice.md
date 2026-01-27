# Linux Practice: Processes and Services
## Process commands
#### `ps` : Shows a report of current processes.
- Output
```
    PID TTY          TIME CMD
  49633 pts/0    00:00:00 bash
  49642 pts/0    00:00:00 ps
```
#### `top` : Display a real time view of running processes.
- Output
```
top - 18:38:39 up 12 days,  8:46,  1 user,  load average: 0.00, 0.00, 0.00
Tasks: 112 total,   1 running, 111 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :    914.2 total,     75.9 free,    395.1 used,    613.8 buff/cache     
MiB Swap:      0.0 total,      0.0 free,      0.0 used.    519.1 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                                                                                                              
      1 root      20   0   22752  14176   9652 S   0.0   1.5   0:21.87 systemd                                                                                                                                                                                              
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.19 kthreadd                                                                                                                                                                                             
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release                                                                                                                                                                               
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_gp                                                                                                                                                                                     
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-sync_wq                                                                                                                                                                                    
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-kvfree_rcu_reclaim                                                                                                                                                                         
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_flushwq                                                                                                                                                                               
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns                                                                                                                                                                                      
     11 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-events_highpri                                                                                                                                                                          
     13 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_percpu_wq                                                                                                                                                                               
     14 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_rude_kthread                                                                                                                                                                               
     15 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_trace_kthread                                                                                                                                                                              
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.78 ksoftirqd/0                                                                                                                                                                                          
     17 root      20   0       0      0      0 I   0.0   0.0   0:18.18 rcu_sched                                                                                                                                                                                            
     18 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_exp_par_gp_kthread_worker/0                                                                                                                                                                      
     19 root      20   0       0      0      0 S   0.0   0.0   0:00.04 rcu_exp_gp_kthread_worker                                                                                                                                                                            
     20 root      rt   0       0      0      0 S   0.0   0.0   0:04.98 migration/0                                                                                                                                                                                          
     21 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                                                                                                                                        
     22 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                                                                                                                                              
     23 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                                                                                                                                              
     24 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1                                                                                                                                                                                        
     25 root      rt   0       0      0      0 S   0.0   0.0   0:04.21 migration/1                                                                                                                                                                                          
     26 root      20   0       0      0      0 S   0.0   0.0   0:00.79 ksoftirqd/1                                                                                                                                                                                          
     28 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/1:0H-events_highpri                                                                                                                                                                          
     29 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kdevtmpfs                                                                                                                                                                                            
     30 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-inet_frag_wq                                                                                                                                                                               
     31 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kauditd                                                                                                                                                                                              
     32 root      20   0       0      0      0 S   0.0   0.0   0:00.39 khungtaskd                                                                                                                                                                                           
```
## Service commands 
#### `systemctl status` : Shows service status.
- Output
```
docker.service - Docker Application Container Engine
     Loaded: loaded (/usr/lib/systemd/system/docker.service; enabled; preset: enabled)
     Active: active (running) since Thu 2026-01-15 09:52:45 UTC; 1 week 5 days ago
TriggeredBy: ● docker.socket
       Docs: https://docs.docker.com
   Main PID: 868 (dockerd)
      Tasks: 9
     Memory: 32.3M (peak: 95.7M)
        CPU: 1min 53.603s
     CGroup: /system.slice/docker.service
             └─868 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock

```
#### `systemctl list-units` : List units that systemd currently has in memory.
- Output
```
  UNIT                                                                         LOAD   ACTIVE SUB       DESCRIPTION                                                                  
  proc-sys-fs-binfmt_misc.automount                                            loaded active running   Arbitrary Executable File Formats File System Automount Point                
  sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1-nvme0n1p1.device      loaded active plugged   Amazon Elastic Block Store cloudimg-rootfs
  sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1-nvme0n1p14.device     loaded active plugged   Amazon Elastic Block Store 14
  sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1-nvme0n1p15.device     loaded active plugged   Amazon Elastic Block Store UEFI
  sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1-nvme0n1p16.device     loaded active plugged   Amazon Elastic Block Store BOOT
  sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1.device                loaded active plugged   Amazon Elastic Block Store
  sys-devices-pci0000:00-0000:00:05.0-net-ens5.device                          loaded active plugged   Elastic Network Adapter (ENA)
  sys-devices-pci0000:00-0000:00:1d.0-nvme-nvme3-nvme3n1.device                loaded active plugged   Amazon Elastic Block Store
  sys-devices-pci0000:00-0000:00:1e.0-nvme-nvme1-nvme1n1.device                loaded active plugged   Amazon Elastic Block Store
  sys-devices-pci0000:00-0000:00:1f.0-nvme-nvme2-nvme2n1.device                loaded active plugged   Amazon Elastic Block Store
  acpid.path                                                                   loaded active running   ACPI Events Check
  systemd-ask-password-console.path                                            loaded active waiting   Dispatch Password Requests to Console Directory Watch
  systemd-ask-password-wall.path                                               loaded active waiting   Forward Password Requests to Wall Directory Watch                            
  init.scope                                                                   loaded active running   System and Service Manager
  session-2124.scope                                                           loaded active running   Session 2124 of User ubuntu                                                  
  acpid.service                                                                loaded active running   ACPI event daemon
  apparmor.service                                                             loaded active exited    Load AppArmor profiles
  apport.service                                                               loaded active exited    automatic crash report generation
  blk-availability.service                                                     loaded active exited    Availability of block devices
  chrony.service                                                               loaded active running   chrony, an NTP client/server
  cloud-config.service                                                         loaded active exited    Cloud-init: Config Stage
```
## Log commands 
#### `journalctl -u <service>` : `journalctl -u ssh` Shows log of ssh service.
- Output
```
Nov 29 17:57:07 ip-172-31-17-215 systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Nov 29 17:57:07 ip-172-31-17-215 sshd[1036]: Server listening on 0.0.0.0 port 22.
Nov 29 17:57:07 ip-172-31-17-215 sshd[1036]: Server listening on :: port 22.
Nov 29 17:57:07 ip-172-31-17-215 systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
Nov 29 17:57:09 ip-172-31-17-215 ec2-instance-connect[1146]: Querying EC2 Instance Connect keys for matching fingerprint: SHA256:pDI8iyjAkpgnwxq8DUPKSspUDi9g/YZwiEKPjrN8mHQ
Nov 29 17:57:09 ip-172-31-17-215 ec2-instance-connect[1178]: Providing ssh key from EC2 Instance Connect with fingerprint: SHA256:pDI8iyjAkpgnwxq8DUPKSspUDi9g/YZwiEKPjrN8mHQ, request-id: 701e876d-1027-425a-98a8-36c36d6663e4, for IAM principal: arn:aws:iam::35637284250>
Nov 29 17:57:10 ip-172-31-17-215 ec2-instance-connect[1295]: Querying EC2 Instance Connect keys for matching fingerprint: SHA256:pDI8iyjAkpgnwxq8DUPKSspUDi9g/YZwiEKPjrN8mHQ
Nov 29 17:57:10 ip-172-31-17-215 ec2-instance-connect[1327]: Providing ssh key from EC2 Instance Connect with fingerprint: SHA256:pDI8iyjAkpgnwxq8DUPKSspUDi9g/YZwiEKPjrN8mHQ, request-id: 701e876d-1027-425a-98a8-36c36d6663e4, for IAM principal: arn:aws:iam::35637284250>
Nov 29 17:57:10 ip-172-31-17-215 sshd[1037]: Accepted publickey for ubuntu from 13.239.158.3 port 48233 ssh2: ED25519 SHA256:pDI8iyjAkpgnwxq8DUPKSspUDi9g/YZwiEKPjrN8mHQ
Nov 29 17:57:10 ip-172-31-17-215 sshd[1037]: pam_unix(sshd:session): session opened for user ubuntu(uid=1000) by ubuntu(uid=0)
Nov 29 21:03:36 ip-172-31-17-215 sshd[7320]: error: maximum authentication attempts exceeded for root from 220.76.214.90 port 54782 ssh2 [preauth]
Nov 29 21:03:36 ip-172-31-17-215 sshd[7320]: Disconnecting authenticating user root 220.76.214.90 port 54782: Too many authentication failures [preauth]
Nov 29 21:44:04 ip-172-31-17-215 systemd[1]: Stopping ssh.service - OpenBSD Secure Shell server...
Nov 29 21:44:04 ip-172-31-17-215 sshd[1036]: Received signal 15; terminating.
Nov 29 21:44:04 ip-172-31-17-215 systemd[1]: ssh.service: Deactivated successfully.
Nov 29 21:44:04 ip-172-31-17-215 systemd[1]: Stopped ssh.service - OpenBSD Secure Shell server.
Nov 29 21:44:04 ip-172-31-17-215 systemd[1]: ssh.service: Consumed 1.372s CPU time, 9.4M memory peak, 0B memory swap peak.
```
#### `tail -n 50` : `tail -n 50 /var/log/auth.log` Print last 50 lines of log file.
- Output
```
2026-01-27T17:08:32.777419+00:00 ip-172-31-17-215 sshd[48978]: banner exchange: Connection from 3.130.96.91 port 33608: invalid format
2026-01-27T17:09:31.370982+00:00 ip-172-31-17-215 sshd[48979]: Connection closed by 3.130.96.91 port 46336
2026-01-27T17:12:22.663048+00:00 ip-172-31-17-215 sshd[48984]: banner exchange: Connection from 3.130.96.91 port 57994: invalid format
2026-01-27T17:14:05.049642+00:00 ip-172-31-17-215 sshd[48985]: Connection closed by 3.130.96.91 port 45542 [preauth]
2026-01-27T17:14:45.687681+00:00 ip-172-31-17-215 sshd[48987]: banner exchange: Connection from 3.130.96.91 port 47294: invalid format
2026-01-27T17:15:01.762388+00:00 ip-172-31-17-215 CRON[48988]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
2026-01-27T17:15:01.766961+00:00 ip-172-31-17-215 CRON[48988]: pam_unix(cron:session): session closed for user root
2026-01-27T17:17:01.794858+00:00 ip-172-31-17-215 CRON[48991]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
2026-01-27T17:17:01.802813+00:00 ip-172-31-17-215 CRON[48991]: pam_unix(cron:session): session closed for user root
2026-01-27T17:25:01.812961+00:00 ip-172-31-17-215 CRON[49019]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
2026-01-27T17:25:01.821065+00:00 ip-172-31-17-215 CRON[49019]: pam_unix(cron:session): session closed for user root
2026-01-27T17:35:01.826559+00:00 ip-172-31-17-215 CRON[49028]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
2026-01-27T17:35:01.830733+00:00 ip-172-31-17-215 CRON[49028]: pam_unix(cron:session): session closed for user root
2026-01-27T17:43:17.092355+00:00 ip-172-31-17-215 sshd[49486]: Accepted publickey for ubuntu from 223.176.61.171 port 65242 ssh2: RSA SHA256:cp5EGYf9Ta606Sbw1FSig0j/aXZNUNRncYXPgU8sGPc
2026-01-27T17:43:17.094258+00:00 ip-172-31-17-215 sshd[49486]: pam_unix(sshd:session): session opened for user ubuntu(uid=1000) by ubuntu(uid=0)
2026-01-27T17:43:17.108980+00:00 ip-172-31-17-215 systemd-logind[576]: New session 2124 of user ubuntu.
2026-01-27T17:43:17.126474+00:00 ip-172-31-17-215 (systemd): pam_unix(systemd-user:session): session opened for user ubuntu(uid=1000) by ubuntu(uid=0)
2026-01-27T17:45:01.836917+00:00 ip-172-31-17-215 CRON[49661]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
2026-01-27T17:45:01.841901+00:00 ip-172-31-17-215 CRON[49661]: pam_unix(cron:session): session closed for user root
2026-01-27T17:55:01.850109+00:00 ip-172-31-17-215 CRON[49702]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
2026-01-27T17:55:01.854459+00:00 ip-172-31-17-215 CRON[49702]: pam_unix(cron:session): session closed for user root
```
## Mini troubleshooting steps
- Step 1: Check service status. If service inactive/fail go to second step.
- Step 2: Check log file.
- Step 3: Find error in logs.
- Step 4: Resolve error.
#### Step 1: Checking service status using command `systemctl status ssh`
- Output
```
ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; disabled; preset: enabled)
    Drop-In: /usr/lib/systemd/system/ssh.service.d
             └─ec2-instance-connect.conf
     Active: active (running) since Thu 2026-01-15 09:53:53 UTC; 1 week 5 days ago
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
   Main PID: 1228 (sshd)
      Tasks: 1 (limit: 1008)
     Memory: 9.2M (peak: 17.0M)
        CPU: 1min 13.384s
     CGroup: /system.slice/ssh.service
             └─1228 "sshd: /usr/sbin/sshd -D -o AuthorizedKeysCommand /usr/share/ec2-instance-connect/eic_run_authorized_keys %u %f -o AuthorizedKeysCommandUser ec2-instance-connect [listener] 0 of 10-100 startups"
```
#### Step 2: Checking log file using command `tail -n 10 /var/log/auth.log`
- Output
```
2026-01-27T17:55:01.850109+00:00 ip-172-31-17-215 CRON[49702]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
2026-01-27T17:55:01.854459+00:00 ip-172-31-17-215 CRON[49702]: pam_unix(cron:session): session closed for user root
2026-01-27T18:05:01.865443+00:00 ip-172-31-17-215 CRON[49730]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
2026-01-27T18:05:01.872124+00:00 ip-172-31-17-215 CRON[49730]: pam_unix(cron:session): session closed for user root
2026-01-27T18:12:06.120165+00:00 ip-172-31-17-215 sshd[49754]: Connection closed by 170.64.229.109 port 47068
2026-01-27T18:12:19.909563+00:00 ip-172-31-17-215 sshd[49755]: Connection closed by authenticating user root 170.64.229.109 port 37562 [preauth]
2026-01-27T18:15:01.878861+00:00 ip-172-31-17-215 CRON[49757]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
2026-01-27T18:15:01.885494+00:00 ip-172-31-17-215 CRON[49757]: pam_unix(cron:session): session closed for user root
2026-01-27T18:17:01.895281+00:00 ip-172-31-17-215 CRON[49767]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
2026-01-27T18:17:01.905501+00:00 ip-172-31-17-215 CRON[49767]: pam_unix(cron:session): session closed for user root 
```
### Everything looks good 
