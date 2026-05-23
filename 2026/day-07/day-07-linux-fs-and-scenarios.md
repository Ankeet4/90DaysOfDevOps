# Day 07 – Linux File System Hierarchy & Scenario-Based Practice

## Part 1 – Linux File System Hierarchy

# /
The root directory is the starting point of the Linux file system. All files and directories start from here.

### Command
```bash
ls -l /
```

### Files/Folders Seen
- home
- etc

### I would use this when...
Navigating the Linux file system.

---

# /home
Contains home directories of normal users.

### Command
```bash
ls -l /home
```

### Files/Folders Seen
- user directories
- personal files

### I would use this when...
Managing user files and documents.

---

# /root
Home directory of the root user.

### Command
```bash
ls -l /root
```

### Files/Folders Seen
- root scripts
- configuration files

### I would use this when...
Performing administrative tasks as root user.

---

# /etc
Contains system and service configuration files.

### Command
```bash
ls -l /etc
```

### Files/Folders Seen
- hostname
- ssh

### I would use this when...
Editing Linux or application configuration files.

---

# /var/log
Stores Linux system and application logs.

### Command
```bash
ls -l /var/log
```

### Files/Folders Seen
- syslog
- auth.log

### I would use this when...
Troubleshooting Linux services and errors.

---

# /tmp
Used for temporary files.

### Command
```bash
ls -l /tmp
```

### Files/Folders Seen
- temp files
- temporary folders

### I would use this when...
Creating temporary files during testing.

---

# /bin
Contains essential Linux command binaries.

### Command
```bash
ls -l /bin
```

### Files/Folders Seen
- bash
- ls

### I would use this when...
Running basic Linux commands.

---

# /usr/bin
Contains user command binaries and installed applications.

### Command
```bash
ls -l /usr/bin
```

### Files/Folders Seen
- python
- vim

### I would use this when...
Using installed applications and tools.

---

# /opt
Contains optional or third-party applications.

### Command
```bash
ls -l /opt
```

### Files/Folders Seen
- external applications
- custom software

### I would use this when...
Installing third-party software manually.

---

# Hands-on Practice

## Find Largest Log Files

### Command
```bash
du -sh /var/log/* 2>/dev/null | sort -h | tail -5
```

### What I Learned
Used to identify large log files consuming disk space.

---

## View Hostname

### Command
```bash
cat /etc/hostname
```

### What I Learned
Displays the hostname of the Linux system.

---

## Check Home Directory

### Command
```bash
ls -la ~
```

### What I Learned
Shows hidden and visible files in the home directory.

---

# Part 2 – Scenario-Based Practice

# Scenario 1 – Service Not Starting

A web application service called `myapp` failed to start after reboot.

## Step 1
### Command
```bash
systemctl status myapp
```

### Why
Checks whether the service is active, failed, or stopped.

---

## Step 2
### Command
```bash
journalctl -u myapp -n 50
```

### Why
Displays recent logs related to the service.

---

## Step 3
### Command
```bash
systemctl is-enabled myapp
```

### Why
Checks whether the service starts automatically on boot.

---

## Step 4
### Command
```bash
systemctl restart myapp
```

### Why
Attempts to restart the failed service.

---

# Scenario 2 – High CPU Usage

The server is slow and CPU usage is high.

## Step 1
### Command
```bash
top
```

### Why
Shows live CPU and memory usage.

---

## Step 2
### Command
```bash
ps aux --sort=-%cpu | head -10
```

### Why
Displays top CPU-consuming processes.

---

## Step 3
### Command
```bash
pgrep nginx
```

### Why
Finds the process ID of a service.

---

## Step 4
### Command
```bash
kill PID
```

### Why
Stops problematic processes if needed.

---

# Scenario 3 – Finding Service Logs

A developer wants Docker service logs.

## Step 1
### Command
```bash
systemctl status docker
```

### Why
Checks Docker service status.

---

## Step 2
### Command
```bash
journalctl -u docker -n 50
```

### Why
Displays the latest Docker logs.

---

## Step 3
### Command
```bash
journalctl -u docker -f
```

### Why
Monitors Docker logs in real time.

---

# Scenario 4 – File Permission Issue

A script is not executing because of permission denied error.

## Step 1
### Command
```bash
ls -l /home/user/backup.sh
```

### Why
Checks current file permissions.

---

## Step 2
### Command
```bash
chmod +x /home/user/backup.sh
```

### Why
Adds execute permission to the script.

---

## Step 3
### Command
```bash
ls -l /home/user/backup.sh
```

### Why
Verifies execute permission was added.

---

## Step 4
### Command
```bash
./backup.sh
```

# What I Learned

- Linux file system hierarchy basics
- Purpose of important Linux directories
- Basic Linux troubleshooting workflow
- How to inspect services and logs
- How to troubleshoot high CPU usage
- How file permissions work in Linux
