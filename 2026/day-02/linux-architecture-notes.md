# Linux Under the Hood

Today I learned some basic concepts about how Linux works internally.  
This is important because Linux is widely used in DevOps, Cloud, and Server Administration.

# Core Components of Linux

## 1. Kernel
- Kernel is the main part of Linux.
- It works between hardware and software.
- It manages:
  - CPU
  - Memory
  - Processes
  - Devices
  - File systems

## 2. User Space
- User space is where users and applications run.
- Commands like `ls`, `pwd`, `top`, and `ps` run in user space.
- User space communicates with kernel using system calls.

## 3. Init / systemd
- `systemd` is the first process started when Linux boots.
- It has PID 1.
- It manages services and background processes.
- It is also used for boot management and logging.

# Process Management in Linux

## How Processes Are Created
- Linux creates processes using `fork()`.
- Child process can load another program using `exec()`.
- Every process has a unique PID (Process ID).

## Process States

| State | Meaning |
|------|------|
| Running | Process is running |
| Sleeping | Waiting for something |
| Stopped | Process is paused |
| Zombie | Process finished but still exists in process table |

---

# What systemd Does

- Starts services during boot
- Stops and restarts services
- Manages background services
- Collects logs using `journalctl`

**#5 Commands I Would Use Daily**

ps aux
top
systemctl
journalctl
kill -9 PID
