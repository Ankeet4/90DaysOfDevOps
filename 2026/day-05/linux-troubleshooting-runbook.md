# Day 05 – Linux Troubleshooting Runbook

## Target Service / Process

Target service selected: `ssh`

Today I practiced a basic Linux troubleshooting workflow by checking system health, monitoring processes, inspecting logs, and verifying network connectivity.

---

# Environment Basics

## uname -a
Used to display Linux kernel and system information.

### Observation
System information and kernel details were displayed correctly.

---

## cat /etc/os-release
Used to check Linux distribution details.

### Observation
Verified the operating system version and distribution.

---

# Filesystem Sanity Checks

## mkdir /tmp/runbook-demo
Used to create a temporary test directory.

### Observation
Directory was created successfully.

---

## cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo
Used to copy a file and verify file permissions.

### Observation
File copied successfully and permissions were visible.

---

# CPU & Memory Snapshot

## top
Used for live monitoring of CPU and memory usage.

### Observation
System resource usage was normal and no unusual CPU spikes were observed.

---

## free -h
Used to check available and used memory.

### Observation
Enough free memory was available and swap usage was low.

---

# Disk & IO Snapshot

## df -h
Used to check disk space usage.

### Observation
Disk usage was within safe limits.

---

## du -sh /var/log
Used to check total size of log files.

### Observation
Log directory size was manageable and not consuming excessive space.

---

# Network Snapshot

## ss -tulpn
Used to check active listening ports and services.

### Observation
SSH service was listening on the expected port.

---

## curl -I http://localhost
Used to test HTTP response from local service.

### Observation
Connection response was received successfully.

---

# Log Checks

## journalctl -u ssh -n 50
Used to check the latest logs related to the SSH service.

### Observation
No recent SSH errors were found in the logs.

---

## tail -n 50 /var/log/syslog
Used to inspect recent system logs.

### Observation
System logs looked normal without critical errors.

---

# Quick Findings

- SSH service was active and running correctly.
- CPU and memory usage were stable.
- Disk space usage was healthy.
- Network ports were working properly.
- No major issues were found in recent logs.

---

# If This Worsens (Next Steps)

## 1. Restart Service
```bash
sudo systemctl restart ssh
Restart the SSH service if it becomes unresponsive.

2. Increase Log Inspection
journalctl -u ssh -f

Monitor logs continuously for real-time troubleshooting.

3. Advanced Troubleshooting

Use tools like:

strace
htop
netstat

to investigate deeper process or network-related issues.

What I Learned :- 
Today I learned how to perform a basic troubleshooting drill in Linux using process monitoring, service inspection, disk checks, network checks, and log analysis. This helped me understand how DevOps engineers troubleshoot systems step by step.
