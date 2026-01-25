# Day 02 – Linux Architecture, Processes, and systemd

## short note :

### The core components of Linux (kernel, user space, init/systemd)
- The core component of linux are the Kernel (the core managing hardware). The user space where application and services run, relies on a set of core components managed by the init system. Systemd (modern init) has evolved into a comprehensive system and service manager that uses an integrated approach.
### How processes are created and managed
- In Linux processes are created using a combination of the fork() and exec() system calls and are managed by the kernel through various tools and signals for scheduling, monitoring, and termination. Every process is a part of a hierarchy, originating from the first init process (PID 1).
### What systemd does and why it matters
- Systemd is a default modern init system and service manager for most Linux distributions, responsible for booting the user space, managing system resources, and controlling services (daemons).
### process states (running, sleeping, zombie, etc.)
- linux process states define what a process is doing, with primary states including Running (R), Sleeping (S), and Zombie (Z). Running processes execute or wait for cpu time, while Sleeping processes wait for events (Interruptible (S) or Uninterruptible (D). Zombies are dead processes awaiting parent acknowledgement while Stopped processes are paused.
### Here are 5 commands that are used daily.
- ls 
- cd
- htop
- mkdir/touch
- ssh, exit
